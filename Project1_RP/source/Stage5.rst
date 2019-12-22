********
Coding 
********

- Following is the Coding structure

- There are 2 folders and thats it !
- Properly everything is stored in them.

- Folder 1  
- Contains API details 
- First we access API services of 3 Websites
	- Element 14 
	- Mouser
	- Digikey 
	- Code is stored on Git hub

- A small example of one API access showed ! - i.e Element14 


.. code-block:: python
	
	import requests
	from pprint import pprint
	def main():
		response = requests.get("http://api.element14.com//catalog/products?term=manuPartNum:C3216X7R1A106M160AC&storeInfo.id=uk.farnell.com&resultsSettings.offset=0&resultsSettings.numberOfResults=1&resultsSettings.refinements.filters=&resultsSettings.responseGroup=medium&callInfo.omitXmlSchema=false&callInfo.callback=&callInfo.responseDataFormat=JSON&callinfo.apiKey=88888888888888888&units=INR")
		output = response.json()
		pprint(output)
	main()


- Folder 2 
	- Folder 2 has Flask Frame Work Details
	- Template , Static and app.py file
	- Templates folder has all HTML files
	- Static folder has all scripting files 
	- App.py is the scripting program keeping in tact everything !
	- Code will be on Github

	- Following code is of App.py file - the scripting file.


.. code-block:: python

	from wtforms import Form,StringField,TextAreaField,PasswordField,validators
	from flask import Flask,render_template,request,flash,redirect,url_for,session,logging,jsonify
	from wtforms import Form,StringField,TextAreaField,PasswordField,validators
	from passlib.hash import sha256_crypt
	from functools import wraps
	import http.client,json
	import requests
	from pprint import pprint
	from zeep import Client


	app = Flask(__name__)

	# single home

	@app.route('/')
	def home():
		return render_template('home.html')
	# single article

	def about():
		return render_template('about.html')

	# Dashboard 
	@app.route('/dashboard')
	def dashboard():
		return render_template('dashboard.html')
	#now the form part start

	@app.route('/select_indent')
	def select_dashboard():
		return render_template('select_indent.html')

	@app .route('/indent1')
	def indent1():
		return render_template('indent_Element14.html')

	@app .route('/indent2')
	def indent2():
		return render_template('indent_Digikey.html')

	@app .route('/indent3')
	def indent3():
		return render_template('indent_Mouser.html')


	#########################################################################
	# ELement 14
	@app .route('/output',methods=['GET','POST'])
	def output():
		if request.method == 'POST':
			manupno = request.form['manup'] #From form we are taking the data.
			response = requests.get("http://api.element14.com//catalog/products?term=manuPartNum:"+manupno+"&storeInfo.id=in.element14.com&resultsSettings.offset=0&resultsSettings.numberOfResults=1&resultsSettings.refinements.filters=&resultsSettings.responseGroup=medium&callInfo.omitXmlSchema=false&callInfo.callback=&callInfo.responseDataFormat=JSON&callinfo.apiKey=888888888888888888888&units=INR")
			json_object = response.json() # remember you converted string to json object using .json and in python json object acts as dictionary.
			print(type(json_object))
			#new_json = (json_object['manufacturerPartNumberSearchReturn']['products'][0])
			html = render_template('output.html',temp=json_object)
			json_object['dict'] = html # python dictionary , then keychanged from python object to json object.
			print(type(json_object));	
			return jsonify(json_object)

	###########################################################################

	if __name__ == '__main__':
		app.secret_key = 'secret123'
		app.run(debug=True)
	   		   
