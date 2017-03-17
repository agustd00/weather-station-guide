# Δοκιμάζοντας τον Μετεωρολογικό Σταθμού

Με όλους τους αισθητήρες συνδεδεμένους, είναι καλό να βεβαιωθείτε ότι ο μετεωρολογικός σταθμός σας καταγράφει δεδομένα και ότι μπορεί να το ανεβάσει στη βάση Oracle.

## Χειρίζοντας τους αισθητήρες
1. Το ανεμόμετρο και το βροχόμετρο μπορούν να χειριστούν καθώς κανένα απο τα δύο δεν καταγράφει δεδομένα εκτός αν κινηθούν σωματικά. Στρίβοντας το ανεμόμετρο και γέρνοντας το βροχόμετρο μπρός και πίσω μερικές φορές καθώς ακολουθείτε τα παρακάτω βήματα θα έχει ως αποτέλεσμα να φορτωθούν τα δεδομένα. 

1. Ανοίξτε ένα τερματικό παράθυρο (**ctrl** + **alt** + **t**) και τότε αλλάξτε το στο ευρετήριο του `μετεωρολογικού σταθμού`:

  ```bash
  cd weather-station
  ```

1. Για να ξεκινήσετε την φόρτωση των δεδομένων του αισθητήρα, πληκτρολογήστε τα παρακάτω στο τερματικό παράθυρο:

  ```bash
  ./log_all_sensors.py
  ```

1. Θα δείτε την έξοδο όπως την δείχνουμε παρακάτω.

  ![](images/test_01.png)

1. Να μην ανησηχείτε για της προϊδοποίησεις για την `Περικοπεί Δεδομένων`. Οι αισθητήρες μετρούνται σε ένα απίστευτο αριθμό σημαντικών ψηφίων, οπότε αυτές οι αξίες περικοπούνται πριν προσθεθούν στη βάση δεδομένων.

## Ανέβασμα στο Oracle

1. Το επόμενο βήμα είναι να ελεγχθεί ότι το λογισμικό είναι ικανό να ανεβάσει δεδομένα στην online βάση δεδομένων της Oracle. Για να ελεγχθεί αυτό, πληκτρολογήστε τα παρακάτω μέσα στον ακροδέκτη(τερματικό παράθυρο):

  ```bash
  sudo ./upload_to_oracle.py
  ```

1. Θα δείτε την έξοδο όπως την δείχνουμε παρακάτω.

  ![](images/test_02.png)

1. Κάθε `Κατάσταση Απόκρισης: 201` μηνημα message means that a row of the local database on your Raspberry Pi was uploaded to the Oracle database. If you receive a different response code, then check that your Raspberry Pi is connected to the network and that it is capable of communicating through any firewalls or proxy servers your network may be using.

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
