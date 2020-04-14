#Replicating figures to Warwickshire and lower levels

This work makes use of public ONS datasets to create the work.

The OA boundaries are from the ONS, as are age population data. They are all taken from the 2018 mid year estimates.

The boundaries SQL is for a PostGIS install.

R0 figures from imperials first paper, and then the later CMMID paper which reduces the number. At this stage the papers aren't peer reviewed.


## TO DO
* Map new boundaries to potentially high risk areas.
* Perform spatial autocorrelation.

## BLOCKERS
* Issues with server installing GDAL still on going although work around found in the meantime.


### Setting the username and pw
switch to ~/.bashrc and add to the bottom.

```bash
export WCC_USER='yourusername'
export POSTGIS_PW='yourpassword'
export POSTGIS_DB_REST_OF_CONN='the rest of the POSTGIS connection string'
```



## Installing GDAL which is a nightmare
You need GDAL version 2.4.1 on LINUX for this to work with Geopandas.



Install guidance for WSL
```bash
wget http://download.osgeo.org/gdal/gdal-2.4.1.tar.gz
tar xvfz gdal-2.4.1.tar.gz
cd gdal-2.4.1
./configure --with-python=/usr/bin/python3
make && sudo make install
sudo ldconfig
```

Now that's installed into linux. You then need to install into python virtual environment. The version of python you need is 2.4.2

```bash
cd ~/covid19
source venv/bin/activate
pip install gdal=2.4.2
```

### Rtree issues with GDAL
Solved by:
```bash
sudo apt install python3-rtree
```

This will then recognise GDAL in the virtual environment.

