# xxx
<html>  index.html
<body>
<form action="NewServlet1" method="post">

Number 1: <input type="text" name="n1"><br><br>
Number 2: <input type="text" name="n2"><br><br>

Operation:
<select name="op">
<option value="+">+</option>
<option value="-">-</option>
<option value="*">*</option>
<option value="/">/</option>
</select>

<br><br>
<input type="submit" value="Calculate">

</form>
</body>
</html>  NewServlet1.java

import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/NewServlet1")

public class NewServlet1 extends HttpServlet {

protected void doPost(HttpServletRequest request, HttpServletResponse response)
throws ServletException, IOException {

response.setContentType("text/html");
PrintWriter out = response.getWriter();

int n1 = Integer.parseInt(request.getParameter("n1"));
int n2 = Integer.parseInt(request.getParameter("n2"));
String op = request.getParameter("op");

int result = 0;

if(op.equals("+"))
    result = n1 + n2;
else if(op.equals("-"))
    result = n1 - n2;
else if(op.equals("*"))
    result = n1 * n2;
else if(op.equals("/"))
    result = n1 / n2;

out.println("<html>");
out.println("<head><title>Result</title></head>");
out.println("<body>");
out.println("<h2>Result is: " + result + "</h2>");
out.println("</body>");
out.println("</html>");

}
}
 
<html>  index.html
<head>
<title>Login Page</title>
</head>

<body>

<h2>Login Form</h2>

<form action="LoginServlet" method="post">

Username:
<input type="text" name="username"><br><br>

Password:
<input type="password" name="password"><br><br>

<input type="submit" value="Login">

</form>

</body>
</html>       LoginServlet.java

import java.io.IOException;
import java.io.PrintWriter;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/LoginServlet")

public class LoginServlet extends HttpServlet {

protected void doPost(HttpServletRequest request, HttpServletResponse response)
throws ServletException, IOException {

response.setContentType("text/html;charset=UTF-8");

PrintWriter out = response.getWriter();

String user = request.getParameter("username");
String pass = request.getParameter("password");

out.println("<html>");
out.println("<head><title>Login Result</title></head>");
out.println("<body>");

if("admin".equals(user) && "1234".equals(pass))
{
out.println("<h2>Welcome " + user + "</h2>");
}
else
{
out.println("<h2>Login Failed!</h2>");
}

out.println("</body>");
out.println("</html>");

}
}
 
### Write a servlet program to demonstrate the Servlet Life Cycle.
LifeCycleServlet.java
import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletConfig;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/LifeCycleServlet")

public class LifeCycleServlet extends HttpServlet {

    // Constructor
    public LifeCycleServlet() {
        System.out.println("I am from default constructor");
    }

    // init method
    @Override
    public void init(ServletConfig config) throws ServletException {
        super.init(config);
        System.out.println("I am from init method");
    }

    // doGet method
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse res)
            throws ServletException, IOException {

        res.setContentType("text/html");
        PrintWriter pw = res.getWriter();

        pw.println("<html>");
        pw.println("<head><title>Servlet Life Cycle</title></head>");
        pw.println("<body>");
        pw.println("<h2>I am from doGet method</h2>");
        pw.println("</body>");
        pw.println("</html>");

        pw.close();
    }

    // destroy method
    @Override
    public void destroy() {
        System.out.println("I am from destroy method");
    }
} 
## Write a Java Swing program to calculate square and cube of a number taken from the user.
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class SquareCubeApp extends JFrame implements ActionListener {

JTextField t1, t2;
JComboBox cb;
JButton b1, b2;

SquareCubeApp() {

setLayout(new FlowLayout());

add(new JLabel("Enter Number"));
t1 = new JTextField(10);
add(t1);

add(new JLabel("Choose"));
cb = new JComboBox(new String[]{"Square","Cube"});
add(cb);

add(new JLabel("Result"));
t2 = new JTextField(10);
t2.setEditable(false);
add(t2);

b1 = new JButton("Calculate");
b2 = new JButton("Clear");

add(b1);
add(b2);

b1.addActionListener(this);
b2.addActionListener(this);

setTitle("Square Cube Calculator");
setSize(300,200);
setVisible(true);
setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
}

public void actionPerformed(ActionEvent e){

if(e.getSource()==b1){

int x = Integer.parseInt(t1.getText());
int y;

if(cb.getSelectedItem().equals("Square"))
y = x*x;
else
y = x*x*x;

t2.setText(String.valueOf(y));
}
else{
t1.setText("");
t2.setText("");
}
}

public static void main(String args[]){
new SquareCubeApp();
}
}
## Aim: Write a java swing program for creating registration form
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class RegistrationFormApp extends JFrame implements ActionListener {

JLabel lblname,lblfname,lblphone,lblemail,lblgender,lblcity,lblAddress;
JTextField name_txt,fname_txt,phone_txt,email_txt;
JRadioButton male,female;
JComboBox jcbcity;
JTextArea add_txtArea,output_txtArea;
JCheckBox chkbox;
JButton submit_btn;

RegistrationFormApp() {

setLayout(null);

JLabel heading_lbl=new JLabel();
heading_lbl.setBounds(250,5,300,40);
heading_lbl.setText("<html><u><b>Registration Form</b></u></html>");

lblname=new JLabel("Name:");
lblname.setBounds(50,80,100,30);

name_txt=new JTextField();
name_txt.setBounds(180,80,180,30);

lblfname=new JLabel("Fathers name :");
lblfname.setBounds(50,120,150,30);

fname_txt=new JTextField();
fname_txt.setBounds(180,120,180,30);

lblgender=new JLabel("Gender:");
lblgender.setBounds(50,160,150,30);

male=new JRadioButton("Male");
male.setBounds(180,160,70,30);

female=new JRadioButton("Female");
female.setBounds(280,160,80,30);

ButtonGroup gender_grp=new ButtonGroup();
gender_grp.add(male);
gender_grp.add(female);

lblcity =new JLabel("City");
lblcity.setBounds(50,200,100,30);

String city[]={"Mumbai","Thane","Pune"};
jcbcity=new JComboBox(city);
jcbcity.setBounds(180,200,120,30);

lblAddress =new JLabel("Address :");
lblAddress.setBounds(50,240,100,30);

add_txtArea= new JTextArea();
add_txtArea.setBounds(180,240,180,100);

lblphone=new JLabel("Phone No. : ");
lblphone.setBounds(50,350,100,30);

phone_txt=new JTextField();
phone_txt.setBounds(180,350,180,30);

lblemail=new JLabel("Email : ");
lblemail.setBounds(50,390,100,30);

email_txt=new JTextField();
email_txt.setBounds(180,390,180,30);

chkbox=new JCheckBox("I accept the terms and conditions");
chkbox.setBounds(50,430,300,30);

submit_btn=new JButton("Submit");
submit_btn.setBounds(180,500,120,40);

output_txtArea=new JTextArea();
output_txtArea.setBounds(420,80,300,350);

add(heading_lbl);
add(lblname); add(name_txt);
add(lblfname); add(fname_txt);
add(lblgender); add(male); add(female);
add(lblcity); add(jcbcity);
add(lblAddress); add(add_txtArea);
add(lblphone); add(phone_txt);
add(lblemail); add(email_txt);
add(chkbox);
add(submit_btn);
add(output_txtArea);

submit_btn.addActionListener(this);

setSize(800,700);
setVisible(true);
setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
}

public void actionPerformed(ActionEvent e) {

if(chkbox.isSelected()) {

String name=name_txt.getText();
String fname=fname_txt.getText();

String gender="Male";
if(female.isSelected())
gender="Female";

String city_name=(String)jcbcity.getSelectedItem();
String add=add_txtArea.getText();
String phone=phone_txt.getText();
String email=email_txt.getText();

output_txtArea.setText(
"Name : " + name +
"\nFather's Name : " + fname +
"\nGender : " + gender +
"\nCity : " + city_name +
"\nAddress : " + add +
"\nPhone no : " + phone +
"\nEmail : " + email
);
}
else{
output_txtArea.setText("Please accept the terms and condition");
}
}

public static void main(String args[]) {
new RegistrationFormApp();
}
} 
# Aim : Write a servlet program to calculate the product of two numbers.
<html>
<head>
<title>Product</title>
</head>

<body>

<form action="test" method="post">

Enter x
<input type="text" name="t1">
<br><br>

Enter y
<input type="text" name="t2">
<br><br>

<input type="submit" value="Product">

</form>

</body>
</html>          test.java (Servlet)
import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.*;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.*;

@WebServlet("/test")

public class test extends HttpServlet {

protected void doPost(HttpServletRequest req, HttpServletResponse res)
throws ServletException, IOException {

res.setContentType("text/html");
PrintWriter pw = res.getWriter();

int x = Integer.parseInt(req.getParameter("t1"));
int y = Integer.parseInt(req.getParameter("t2"));

int z = x * y;

pw.println("<html>");
pw.println("<body>");
pw.println("<h2>Product of " + x + " and " + y + " is " + z + "</h2>");
pw.println("</body>");
pw.println("</html>");
}
}

 
#### dateTime.jsp
<%@ page contentType="text/html" import="java.util.*" %>
<html>
<head>
<meta http-equiv="refresh" content="1">
<title>Date Time</title>
</head>

<body>

<%
Date d = new Date();
out.println(d.toString());
%>

</body>
</html>

## Write a JavaBean program to display current date and time.
GetTime.jsp
<%@page contentType="text/html" %>
<%@page pageEncoding="UTF-8" %>

<html>
<head>
<title>Current Time</title>
</head>

<body>

<jsp:useBean id="cal" class="GetTime.CalendarBean1"/>

<pre>
Time:   <jsp:getProperty name="cal" property="time"/>

Hour:   <jsp:getProperty name="cal" property="hour"/>

Minute: <jsp:getProperty name="cal" property="minute"/>

Second: <jsp:getProperty name="cal" property="second"/>
</pre>

</body>
</html>

2️⃣ CalendarBean1.java
package GetTime;

import java.util.Calendar;
import java.util.Date;

public class CalendarBean1 {

private Calendar calendar;

public CalendarBean1(){
calendar = Calendar.getInstance();
}

public Date getTime(){
return calendar.getTime();
}

public int getHour(){
return calendar.get(Calendar.HOUR_OF_DAY);
}

public int getMinute(){
return calendar.get(Calendar.MINUTE);
}

public int getSecond(){
return calendar.get(Calendar.SECOND);
}

}
