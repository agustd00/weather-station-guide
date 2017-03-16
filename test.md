# Δοκιμάζοντας τον Μετεωρολογικό Σταθμού

Με όλους τους αισθητήρες συνδεδεμένους, είναι καλό να βεβαιωθείτε ότι ο μετεωρολογικός σταθμός σας καταγράφει δεδομένα και ότι μπορεί να το ανεβάσει στη βάση Oracle.

## Χειρίζοντας τους αισθητήρες
1. Το ανεμόμετρο και το βροχόμετρο μπορούν να χειριστούν καθώς κανένα απο τα δύο δεν καταγράφει δεδομένα εκτός αν κινηθούν σωματικά. Στρίβοντας το ανεμόμετρο και γέρνοντας το βροχόμετρο μπρός και πίσω μερικές φορές καθώς ακολουθείτε τα παρακάτω βήματα θα έχει ως αποτέλεσμα να φορτωθούν τα δεδομένα. 

1. Ανοίξτε ένα τερματικό παράθυρο (**ctrl** + **alt** + **t**) and then change into the `weather-station` directory:

  ```bash
  cd weather-station
  ```

1. To start logging sensor data, type the following into the terminal window:

  ```bash
  ./log_all_sensors.py
  ```

1. You should see output as shown in the screen capture below.

  ![](images/test_01.png)

1. Do not worry about the `Data truncated` warnings. The sensors measure to an unrealistic number of significant figures, so these values are truncated before they are added to the database.

## Upload to Oracle

1. The next step is to test that the software is capable of uploading the data to the online Oracle Database. To test this, type the following into the terminal:

  ```bash
  sudo ./upload_to_oracle.py
  ```

1. You should see output as shown the screen capture below.

  ![](images/test_02.png)

1. Each `Response status: 201` message means that a row of the local database on your Raspberry Pi was uploaded to the Oracle database. If you receive a different response code, then check that your Raspberry Pi is connected to the network and that it is capable of communicating through any firewalls or proxy servers your network may be using.

## Checking the online database

1. In your web browser, navigate to the [Oracle Database](https://apex.oracle.com/pls/apex/f?p=81290:LOGIN_DESKTOP:0:::::&tz=1:00) and log in:

  ![](images/test_03.png)

1. On your dashboard, click on Weather Measurement to view the latest measurements from your Weather Station.

  ![](images/test_04.png)

1. It is worth having a play around with the filters and the download options with your data, to see what can be achieved.

## What Next?

Now that you have tested your Weather Station, close up the boxes with the long screws and ensure the grommets are in place. 

  ![](images/close_up_station.png)

You can then proceed to the next section, and learn how to [install the Weather Station at your school](siting.md).
