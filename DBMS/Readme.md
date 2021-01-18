## Simple GUI program Connecting Java and DBMS (Mariadb is used here)
(if you use mysql change all occuring of Mariadb to mysql in the source code)

## To start open up your mariadb/sql shell:
### Now create a database named studenId
~~~
create database studentId;
~~~
![database](https://github.com/TheAmalShibu/JAVA/blob/main/DBMS/Asset/1.png)
### Now create a table list for inserting Name,Age and RollNo
~~~
create table list(Name varchar(10),Age int(3),RollNo int(3));
~~~
![Table](https://github.com/TheAmalShibu/JAVA/blob/main/DBMS/Asset/2.png)
![descanddetails](https://github.com/TheAmalShibu/JAVA/blob/main/DBMS/Asset/3.png)
## The GUI based JAVA code for inserting Name,Age and RollNo to the Database
### File name ```studentList.java```
```
import javax.swing.*;  
import java.awt.event.*; 
import java.sql.*; 
public class studentList implements ActionListener
{  
        JTextField tf1,tf2,tf3;  
        JButton b1;  
        studentList()
	    {  
            JFrame f= new JFrame("Student Details");  
            f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

            //The buttons

            JLabel l1,l2,l3;  
            l1=new JLabel("Name:");  
            l1.setBounds(50,20, 100,30);
            l2=new JLabel("Roll No:");  
            l2.setBounds(50,70, 600,30);
            l3=new JLabel("Age");  
            l3.setBounds(50,120, 600,30);

            tf1=new JTextField();  
            tf1.setBounds(50,50,350,20);  
            tf2=new JTextField();  
            tf2.setBounds(50,100,350,20);
            tf3=new JTextField();  
            tf3.setBounds(50,150,350,20);  

            b1=new JButton("Update List");  
            b1.setBounds(50,200,250,30);  
            b1.addActionListener(this);  


            f.add(tf1);f.add(tf2);f.add(b1);f.add(tf3);f.add(l1);f.add(l2);f.add(l3);
            f.setSize(800,400);  
            f.setLayout(null);  
            f.setVisible(true);  
        }         
        public void actionPerformed(ActionEvent e)
    	{  
            String Name=tf1.getText(); 
            int roll= Integer.parseInt(tf2.getText()); 
            int age= Integer.parseInt(tf3.getText()); 



            try 
            {
                // Register JDBC driver
                //Class.forName("org.mariadb.jdbc.Driver");
                //Open a connection
                Connection con=DriverManager.getConnection("jdbc:mariadb://localhost:3306/studentid","root","amalshibu");
		//Connection con=DriverManager.getConnection("jdbc:mariadb://localhost:3306/studentid","username","password");
                //Create a statement object
                Statement st=con.createStatement();
                st.executeUpdate("insert into list(Name,Age,RollNo) values('"+Name+"','"+age+"','"+roll+"')") ;
                //value hopefully inserted
                con.close(); //Close the connection
            }
            catch(SQLException error) 
            { 
                System.out.println("Error is " +error); 
            } 
        }  

    public static void main(String amal[])throws ClassNotFoundException
    {   
        studentList aa=new studentList();
    }
}  

```
![The GUI](https://github.com/TheAmalShibu/JAVA/blob/main/DBMS/Asset/resultbox.png)
![Updated Database](https://github.com/TheAmalShibu/JAVA/blob/main/DBMS/Asset/op.png)
