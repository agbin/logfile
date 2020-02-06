# Log_Analyzer
Log Analyzer is a Python parsing script that allow you to easily analyze log files generated by Gunicorn Server.

The script has the following features:
console application
An application that uses python 3.8 without external dependencies (Pytest is used to write tests)
The application receives the name of the file containing the correct output of the Gunicorn server

### The script allows printing statistics for a given time period (or all):
Number of queries
Average number of queries per second
Number of individual server response codes (200: 10, 301: 20, 500: 56 etc.)
Average size of generated response (for queries with the code 2xx)

## Example usage:

```
1) Example call:
python3.8 parser.py --from 01-10-2019_11-23-11 --to 01-12-2020_01-33 logfile.log
or
python3 parser.py --from 01-10-2019_11-23-11 --to 01-12-2020_01-33 logfile.log
Example output:
from: 2019-10-01 11:23:11
to: 2020-12-01 01:33:00

requests: 96202
requests/sec: 0.0026
responses: {'200': 96205, '404': 3794}
avg size of 2xx responses: 0.0059143087158410644 Mb
```
2) Example call:
python3 parser.py --from 01-10-2019_11-23-11 logfile.log

Example output:
```
ZOSTANIE UZYTA DOMYSLNA DATA KONCOWA, --to: 2020-01-08 14:04:44 , gdyż wystąpił jeden z przypadków: 1) NIEPOPRAWNY FORMAT SŁOWA '--to' 2) BRAK SŁOWA '--to' 3) NIEPOOPRAWNY FORMAT DATY KONCOWEJ 3) DATA KONCOWA NIE ZOSTALA PODANA

from: 2019-10-01 11:23:11
to: 2020-01-08 14:04:44

requests: 96202
requests/sec: 0.0112
responses: {'200': 96205, '404': 3794}
avg size of 2xx responses: 0.0059143087158410644 Mb
```

3) Example call:
python3 parser.py --to 01-12-2020_01-33 logfile.log

Example output:
```
ZOSTANIE UZYTA DOMYSLNA DATA POCZATKOWA, --FROM: 2019-09-06 08:39:18 , gdyż wystąpił jeden z przypadków: 1) NIEPOPRAWNY FORMAT SŁOWA '--from' 2) BRAK SŁOWA '--from' 3) NIEPOOPRAWNY FORMAT DATY POCZATKOWEJ3) DATA POCZATKOWA NIE ZOSTALA PODANA

from: 2019-09-06 08:39:18
to: 2020-12-01 01:33:00

requests: 96202
requests/sec: 0.0025
responses: {'404': 3794, '200': 96205}
avg size of 2xx responses: 0.0059143087158410644 Mb
```

4) Example call:
python3 parser.py logfile.log

Example output:
```
ZOSTANIE UZYTA DOMYSLNA DATA POCZATKOWA, --FROM: 2019-09-06 08:39:18 , gdyż wystąpił jeden z przypadków: 1) NIEPOPRAWNY FORMAT SŁOWA '--from' 2) BRAK SŁOWA '--from' 3) NIEPOOPRAWNY FORMAT DATY POCZATKOWEJ3) DATA POCZATKOWA NIE ZOSTALA PODANA
ZOSTANIE UZYTA DOMYSLNA DATA KONCOWA, --to: 2020-01-08 14:04:44 , gdyż wystąpił jeden z przypadków: 1) NIEPOPRAWNY FORMAT SŁOWA '--to' 2) BRAK SŁOWA '--to' 3) NIEPOOPRAWNY FORMAT DATY KONCOWEJ 3) DATA KONCOWA NIE ZOSTALA PODANA

from: 2019-09-06 08:39:18
to: 2020-01-08 14:04:44

requests: 96202
requests/sec: 0.0090
responses: {'404': 3794, '200': 96205}
avg size of 2xx responses: 0.0059143087158410644 Mb
```

