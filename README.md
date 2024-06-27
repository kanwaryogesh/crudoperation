# crudoperation
CRUD OPERATION ON PYTHON MYSQL OPERATION
import mysql.connector
# Step1:-Connect to the MySQL Database#
try:
  conn=mysql.connector.connect(
   host="127.0.0.1",
   user="root",
   password="passyk@",
   database="crud_python"
 )
  mycursor=conn.cursor()
  print("Connection Established")
except:
    print("Connection Error")
# Step2:-#Create a Database.
#mycursor.execute("CREATE DATABASE crud_python")
#conn.commit()

#print("DATABASE CREATED")
#Step3:-Create a Table.
#name,age,id and email
mycursor.execute(
    '''
      CREATE TABLE customers(
  id INTEGER PRIMARY KEY,
  name VARCHAR(50) NOT NULL,
  email VARCHAR(50) NOT NULL,
  age INTEGER
  )
  ''')
conn.commit()
print("Table is Created")

#Step4:-Insert New Records into "Customers" Table.

#mycursor.execute(

#"""
#INSERT INTO Customers VALUES
#(1,"Anil","anil@gmail.com",40),
#(2,"Rahul","rahul@lgmail.com",24),
#(3,"Parth","parth@gmail.com",34)
  
#""")
#conn.commit()
#print("Rows are inserted")
#Step5:-Read: Select Data From a Table.
mycursor.execute("select * from customers")
myresult=mycursor.fetchall()

print(myresult)
for x in myresult:
    print(x[1])
#Step6-UPDATE:-Update data in a Table.

mycursor.execute("update customers set age=14 where id=1")
conn.commit()
print("Updated")

#Step7:-DELETE-Delete data from a table.
mycursor.execute("delete from customers where id=1")
conn.commit()
print("Deleted")
