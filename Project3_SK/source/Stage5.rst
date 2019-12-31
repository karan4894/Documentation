********
Coding 
********

- Following is the Coding structure

- App.py file contains the main scripting program.
- Template folder contains HTML files.
- Static folder contains - CSS and Javascript files.
- Code will be in available on github.
- The application contains Mysql and Datatables together.


.. code-block:: python
	
	from flask import Flask,request,render_template,session,redirect,url_for,flash
	import pymysql
	import bcrypt
	from functools import wraps
	app = Flask(__name__)

	mydb = pymysql.connect(host="localhost",user="KP_mysql",password="KP_mysql1",db="karan",charset='utf8mb4',cursorclass=pymysql.cursors.DictCursor)

	print ("Connection successful !")
	print(mydb)

	#<!---------------------------------------------------------------------------------------------------------------->

	@app.route('/home')
	def home_outside():   
		return render_template('home.html')






	@app.route('/',methods=['GET','POST'])
	def dashboard():
		cursor = mydb.cursor()
		sql = ('SELECT * FROM BOM')
		cursor.execute(sql)
		myresult = cursor.fetchall()
		cursor.close()
		return render_template('home.html',data=myresult)

	#<!---------------------------------------------------------------------------------------------------------------->


	@app.route('/signup',methods=['GET','POST'])
	def register():
		if request.method == 'GET':
			return render_template('register.html')
		else:	
			first_name = request.form['first_name']
			last_name = request.form['last_name']
			password = request.form['password']
			confirm_password = request.form['confirm_password']
			if password == confirm_password:
				password = request.form['password'].encode('utf-8')
				hash_password = bcrypt.hashpw(password,bcrypt.gensalt())
				cursor = mydb.cursor()
				sql = ('INSERT INTO LOG(first_name,last_name,passwd) VALUES (%s,%s,%s)')
				cursor.execute(sql,(first_name,last_name,hash_password))
				session['first_name'] = first_name
				session['last_name'] = last_name
				mydb.commit()
				cursor.close()
				return redirect(url_for('login'))
			else:
				flash("Please check registration process")
				return render_template('register.html')

	#<!---------------------------------------------------------------------------------------------------------------->




	@app.route('/login',methods=['GET','POST'])
	def login():
			if request.method == 'POST':
				first_name = request.form['first_name']
				password = request.form['password'].encode('utf-8')
				cursor = mydb.cursor()
				sql = ('SELECT * FROM LOG WHERE first_name=%s')
				cursor.execute(sql,(first_name))
				result = cursor.fetchone()
				print(result)
				if len(result)> 0:
					if bcrypt.hashpw(password,result['passwd'].encode('utf-8')) == result['passwd'].encode('utf-8'):
						session['logged_in'] = True
						session['first_name'] = result['first_name']
						return render_template('dashboard.html')
					else:
						flash("Check Username or Password !")
						cursor.close()
						return render_template('login.html')
			return render_template('login.html')

	#<!---------------------------------------------------------------------------------------------------------------->

	# check if user logged in

	def is_logged_in(f):
		@wraps(f)
		def wrap(*args, **kwargs):
			if 'logged_in' in session:
				return f(*args, **kwargs)
			else:
				flash('Unauthorized, Please Login','danger')
				return redirect(url_for('login'))
		return wrap
	#<!---------------------------------------------------------------------------------------------------------------->

	@app.route('/logout')
	def logout():
		session.clear()
		return render_template('home.html')
	#<!---------------------------------------------------------------------------------------------------------------->

	@app.route('/mysql_page',methods=['GET','POST'])
	@is_logged_in
	def output():
		if request.method == 'POST':
			p1 = request.form['para1']
			p2 = request.form['para2']
			cursor = mydb.cursor()
			sql = 'INSERT INTO BOM(para1,para2) VALUES (%s,%s)'
			cursor.execute(sql,(p1,p2))
			mydb.commit()
			#############################################################
			sql = 'SELECT * FROM BOM' 
			cursor.execute(sql)
			myresult = cursor.fetchall()
			cursor.close()
			return render_template('mysql_page.html',data=myresult)
		return render_template('mysql_page.html')

	#<!---------------------------------------------------------------------------------------------------------------->

	@app.route('/index',methods=['GET','POST'])
	def index():
		if request.method == 'POST':
			p1 = request.form['para1']
			p2 = request.form['para2']
			cursor = mydb.cursor()
			sql = 'INSERT INTO BOM(para1,para2) VALUES (%s,%s)'
			cursor.execute(sql,(p1,p2))
			mydb.commit()
			#############################################################
			sql = 'SELECT * FROM BOM' 
			cursor.execute(sql)
			myresult = cursor.fetchall()
			cursor.close()
			return render_template('index.html',data=myresult)
		return render_template('index.html')





	#<!---------------------------------------------------------------------------------------------------------------->


	@app.route('/update',methods=['GET','POST'])
	def update():
		if request.method == 'POST':
			id_new = request.form['id']
			p1_nw = request.form['para1_new']
			p2_nw = request.form['para2_new']
			cursor = mydb.cursor()
			cursor.execute("UPDATE BOM SET para1=%s , para2=%s WHERE id=%s",(p1_nw,p2_nw,id_new,))
			mydb.commit()
			return render_template('mysql_page.html')
		else:
			return render_template('mysql_page.html')
	#<!---------------------------------------------------------------------------------------------------------------->


	@app.route('/delete/<string:id_new>',methods=['GET'])
	def delete(id_new):
		cursor = mydb.cursor()
		cursor.execute("DELETE FROM BOM WHERE id=%s",(id_new,))
		mydb.commit()
		return render_template('mysql_page.html')

	#<!---------------------------------------------------------------------------------------------------------------->

	@app.route('/datatables')
	def datatable():
		return render_template('datatables.html')


	@app.route('/people')
	def people():
		return render_template('people.html')

	if __name__ == '__main__':
		app.secret_key = "1234jmdjnjkhuqtq"
		app.run(debug=True)
