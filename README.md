# Hibernate_inheritance_Single_Table
This project helps to create Hierarchical Inheritance (one base class and many subclasses) in Hibernate. The data from all its subclasses are appended in the table generated from the base class.
Here, 
In this example, Create a Maven Project Called HiberInheritance
i) A base class **Employee** with two variabels employee number as eno and employee name as ename.
ii) First sub class as **FullTimeEmployee** with a variable salary
iii)Another sub class as **PartTimeEmployee** with a variable amount
In all the three classes, generate getters and setters for the fileds(variables) created in these classes; **annotate all the classes with @Entity annotation**
**Steps consider for Single_Table**
a. Go to Employee class and annotate with the inheritance strategy called **@Inheritance(strategy=InheritanceType.SINGLE_TABLE)**
and a new column that we want to create is done with **@DiscriminatorColumn(name="Type", discriminatorType=DiscriminatorType.STRING)**. Here, a new column is creared with name "Type" and the data stored inside is of type string.

b. Then, go to each Subclass and annotate the class **FullTimeEmployee** class with **@DiscriminatorValue("FT")** and the class **PartTimeEmployee** with **@DiscriminatorValue("PT")**.
   The idea here is, whenever an objet is created for **FullTimeEmployee** class, **FT** will be added in the base table **Type** column. Similarly for **PartTimeEmployee** **PT**.

Finally, in **hibernate.cfg.xml** file, give mapping element and assign each class.

Now, Write the Main class to create main method:
a. Inside create SessionFactory, Session, Transaction objects; objects to **FullTimeEmployee** and **PartTimeEmployee** classes and call the setters of two classes. Then, save the two objects.

**Run the main method to see the desired output**
Now, go to MySQL and check the employee table and you can see the data from the subclasses are getting fetched into the based table employee and a new column is getting generated with name Type and the values of the column are either **FT** or **PT**

