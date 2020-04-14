#Replicating figures to Warwickshire and lower levels


## TO DO
* Happy with the model now, now data link.
* Two datasets of interest population density and then lsoa

## BLOCKERS
Currently the server doesn't have GDAL - geopandas is the worst!!

## Useful bash - quick reference
cp -r /mnt/c/Users/tfos1/"OneDrive - Warwickshire County Council"/Documents/covid19 ~/covid19/data/
mv covid19/data/covid19/S* covid19/data/
rm -rf covid19/data/covid19

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

