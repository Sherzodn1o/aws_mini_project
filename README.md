University Timetable Application.
Sherzod Saidjonov.
This project is created for the COSC 2610 4T 2024 FA Operating Systems course.
It is a web application designed to display university course timetables, developed using Flask and hosted on an AWS EC2 instance, with the PostgreSQL database managed through AWS RDS.
Users can select their academic level (Undergraduate or Graduate) and view a timetable of available courses.

Available Features:
Developed using the Flask web framework.
PostgreSQL database for storing and managing course data.
Deployed on AWS (EC2 for hosting, RDS for database storage).

Technologies Used:
Python (Flask framework)
PostgreSQL
AWS EC2 (for hosting)
AWS RDS (for database)

Setup and Deployment Instructions:
1. Set Up AWS Resources:
Sign up for an AWS account and log in.
Launch an EC2 instance and configure the required security groups.
Create a PostgreSQL database on AWS RDS with public access enabled.

2. Connect to the EC2 Instance using the following command to SSH into your EC2 instance:
ssh -i "C:\your_key_2_ec2.pem" ubuntu@<EC2_Public_IP>

3. Prepare the EC2 Instance Update the instance and install necessary dependencies:
sudo apt update
sudo apt install python3 python3-pip postgresql-client -y


Also, I needed to establish connection on aws website itself between my ec2 instance and rds database.

4. Connect to the RDS PostgreSQL Database using the command below to connect to the PostgreSQL database:
psql -h <RDS_End_Point> -U <RDS_User> -d <RDS_Database_Name>
Set Up the Database Table Create the timetable table by executing the following SQL commands:
CREATE TABLE timetable (
    id SERIAL PRIMARY KEY,
    course_name VARCHAR(100),
    level VARCHAR(20),
    day VARCHAR(20),
    time VARCHAR(20)
);

INSERT INTO timetable (course_name, level, day, time)
VALUES
    ('Computer Languages', 'Undergraduate', 'Wednesday', '2:00 PM'),
    ('Operating Systems', 'Graduate', 'Tuesday', '2:00 PM'),
    ('Database Concepts', 'Graduate', 'Tuesday', '11:30 AM'),
    ('College Algebra', 'Undergraduate', 'Thursday', '9:00 AM'),
    ('Political Theory', 'Undergraduate', 'Monday', '4:20 PM');
    
5. Set Up the Flask Application Create a project directory:
mkdir my_project
cd my_project
touch app.py

Implement the Flask application in app.py to establish a connection to the PostgreSQL database.

6. Design HTML templates create a templates directory and add index.html and timetable.html files, containing the required HTML structure.

7. Set Up a Virtual Environment and then activate a Python virtual environment:
python3 -m venv venv
source venv/bin/activate
Then install the following package:
pip3 install pg8000

8.Install Required Python Libraries Install the necessary Python libraries:
pip3 install --upgrade pip
pip3 install flask psycopg2-binary

9. Run the Flask Application Start the Flask application by running:
python app.py

Access the Application Open a web browser and visit:
http://<EC2_Public_IP>:8000
