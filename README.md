Educational Organisation Using ServiceNow
Category: ServiceNow

Skills Required:
-----------------
HTML,CSS,Javascript
Project Description:
---------------------
The Educational Management System is a comprehensive platform designed to streamline administrative tasks within educational institutions. It facilitates efficient management of student and teacher data, simplifies the admission process, and provides tools for monitoring student progress.

Skill Tags:-
-------------
1)Sign up for a developer account on the ServiceNow Developer site “https://developer.servicenow.com”.
2)Once logged in, navigate to the "Personal Developer Instance" section.
3)Click on "Request Instance" to create a new ServiceNow instance.
4)Fill out the required information and submit the request.
5)You'll receive an email with the instance details once it's ready.
6)Log in to your ServiceNow instance using the provided credentials.
7)Now you will navigate to the ServiceNow.

SECTION 1: Creating a update set
------------
1.Click on All >> Local update sets.
2.Click on new
3.Enter the Details Name: Educational Organisation >> Click on Submit and make Current.

SECTION 2: Creating Salesforce Table, Creating Admission table and creating Student Progress table
-----------
1)All >> Tables.
2)Click on new
3)Enter the Label(Anything you want): Salesforce >> Click on Name it will Automatically generate Api name.
4)Create columns as given below,Double Click on Column label and Enter the Column labels and click on the tick mark >> Give Type as given .
5)For “Admin Number” Give Display as True and right click on the toggle bar on top >> save
6)Click on controls >> Enable Extensible.
7)Click on “Admin Number” column, In Related Links Click on Advanced View >> Default View (Enable Use dynamic default) >> select Get Next Padded Number in Dynamic default value >> Update .
8)Click on “Grade” Column >> Click on Choices and give Label,Value and Sequence as given below. 


1)Create an Admission Table with Columns given.
2)Select Extends Table >> Salesforce and also Select Add module to menu >> Salesforce.
3)Create Fields as shown
4)Create choice for Admin Status as:
5)Create choice for Pincode as:
6)Create choice for Purpose of Join as:
7)Create choice for School as:

1)Create a Student Progress Table with Columns given.
2)Select Add module to menu >> Salesforce.
3)Create Fields as shown:

SECTION 3:  Configuring Table form for Student Progress Table
-----------
1)In the Student Progress Table Page , Click on Layout form .
2)Click on Admission Number [+] .
3)Select below Admission Number fields in Available side and send it to selected side as below >> save.

SECTION 4:  Creating Form Design for Salesforce, Admission and Student Progress tables
----------
1)All >> System Definition >> Tables .
2)In Label Search for Salesforce and open .
3)Right Click on top Toggle >> Configure >> Form Design.
4)In drop down select Salesforce(u_salesforce).
5)Drag and drop the fields to the left side as below.
6)Save.

1)Follow the same steps as Activity1,Configure the fields as below and Save.

1)Follow the same steps as Activity1,Configure the fields as below and Save

SECTION 4:  Creating Number Maintenance for Admin Number
----------
1)All >> Number Maintenance >> New
2)Fill the details >> Submit.

SECTION 5: Creating Process Flow for Admission Table
-----------
1)All >>Process Flow>> New.
2)Fill the Details as given Below
3)Right Click on toggle and click on the save .
4)Replace the Name and Label as below and click on Insert on stay.
5)Replace the Name and Label in order and click on Insert on stay.
6)Joined >> Rejected >> Rejoined >> Closed >> Cancelled.
7)Order should be New >> InProgress >>Joined >> Rejected >> Rejoined >> Closed >> Cancelled.

SECTION 6: Creating Client Scripts: 
-----------
All >> Client Scripts >> New.
Fill the Details as given.

Write the Code as below, Enable Isolate script and Save.
function onChange(control, oldValue, newValue, isLoading, isTemplate) {
   if (isLoading || newValue === '') {

      return;

   }
   //Type appropriate comment here, and begin script below
   var a = g_form.getReference('u_admission_number');
   g_form.setValue('u_admin_date',a.u_admin_date);
   g_form.setValue('u_grade',a.u_grade);
   g_form.setValue('u_student_name',a.u_student_name);
   g_form.setValue('u_father_name',a.u_father_name);
   g_form.setValue('u_mother_name',a.u_mother_name);
   g_form.setValue('u_father_cell',a.u_father_cell);
   g_form.setValue('u_mother_cell',a.u_mother_cell);
   g_form.setDisabled('u_admin_date',a.u_admin_date);
   g_form.setDisabled('u_grade',a.u_grade);
   g_form.setDisabled('u_student_name',a.u_student_name);
   g_form.setDisabled('u_father_name',a.u_father_name);
   g_form.setDisabled('u_mother_name',a.u_mother_name);
   g_form.setDisabled('u_father_cell',a.u_father_cell);
   g_form.setDisabled('u_mother_cell',a.u_mother_cell);
}

Note: Make sure the Field names should be the same as you created .


Fill the Details as given.
Write the Code as below, Enable Isolate script and Save.
function onChange(control, oldValue, newValue, isLoading, isTemplate) {
   if (isLoading || newValue === '') {

      return;
   }

    var a = g_form.getValue('u_pincode');

if(a == '509358')
{
g_form.setValue('u_mandal', 'kadthal');
g_form.setValue('u_city', 'kadthal');
g_form.setValue('u_district', 'RangaReddy');

}
else if(a == '500081')
{
g_form.setValue('u_mandal', 'karmanghat');
g_form.setValue('u_city', 'karmanghat');
g_form.setValue('u_district', 'RangaReddy');
}
else if(a == '500079')
{
g_form.setValue('u_mandal', 'Abids')
g_form.setValue('u_city', 'AsifNagar');
g_form.setValue('u_district', 'Hyderabad')
}
   //Type appropriate comment here, and begin script below
}


Fill the Details as given.
Write the Code as below, Enable Isolate script and Save.
function onLoad() {
   //Type appropriate comment here, and begin script below
   g_form.setDisabled('u_total',true);
   g_form.setDisabled('u_percentage',true);
   g_form.setDisabled('u_result',true);
}


Fill the Details as given.
Write the Code as below, Enable Isolate script and Save.
function onChange(control, oldValue, newValue, isLoading, isTemplate) {
   if (isLoading || newValue === '') {
      return;
   }
   //Type appropriate comment here, and begin script below
if (newValue){
var a = parseInt(g_form.getValue('u_telugu'));
var b = parseInt(g_form.getValue('u_hindi'));
var c = parseInt(g_form.getValue('u_english')); 
var d = parseInt(g_form.getValue('u_maths'));
var e = parseInt(g_form.getValue('u_science')); 
var f = parseInt(g_form.getValue('u_social'));
var Total = parseInt(a+b+c+d+e+f);
g_form.setValue('u_total', Total);
}
}



Fill the Details as given.

Write the Code as below, Enable Isolate script and Save.
function onChange(control, oldValue, newValue, isLoading, isTemplate) {
   if (isLoading || newValue === '') {
      return;
   }
   //Type appropriate comment here, and begin script below
   if(newValue) {
      var a = parseInt(g_form.getValue('u_percentage')); // Convert the value to an integer for comparison
      if(a >= 0 && a <= 59){
         g_form.setValue('u_result','Fail');
      } else if(a >= 60 && a <= 100) {
         g_form.setValue('u_result','Pass');
      } else {
         // Handle the case if a is out of range (optional)
         g_form.addErrorMessage('Percentage should be between 0 and 100.');
         g_form.clearValue('u_result');
      }
   }
}



Fill the Details as given.
Write the Code as below, Enable Isolate script and Save.
function onChange(control, oldValue, newValue, isLoading, isTemplate) {
   if (isLoading || newValue === '') {
      return;
   }
   //Type appropriate comment here, and begin script below
   var Total = g_form.getValue('u_total');
   var Percentage = (Total/600)*100;
   g_form.setValue('u_percentage',Percentage+'%');
}

