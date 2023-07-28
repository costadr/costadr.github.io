# How to connect to a Postgresql, insert a line and select all lines
```console
import psycopg2


def connect_to_postgresql(host, database, user, password):
    try:
        connection = psycopg2.connect(
            host=host,
            database=database,
            user=user,
            password=password
        )
        cursor = connection.cursor()
        print("Connected to PostgreSQL database")

        cursor.execute("""
            INSERT INTO mytable
            (first_name, last_name, age, email)
            VALUES
            ('Diogo', 'Costa', 37, 'diogo_cost@hotmail.com');
        """)

        cursor.execute("SELECT * from mytable;")
        rows = cursor.fetchall()
        for row in rows:
            print(row)

        cursor.close()
        connection.close()

    except (Exception, psycopg2.Error) as error:
        print("Error while connecting to PostgreSQL:", error)


host = "localhost"
database = "newtests"
user = "postgres"
password = "123"

connect_to_postgresql(host, database, user, password)
```
