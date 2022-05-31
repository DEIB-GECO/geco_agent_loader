# Geco Agent Loader

This software enables the loading of GDM region data files to a database. 

It is typically used in combination with the data integration pipeline [Metadata-Manager](https://github.com/DEIB-GECO/Metadata-Manager), which creates a database for storing the metadata of the integrated datasets during the Mapper, Normalizer/Enricher and Constraint Checker stages. This software complements the database by inserting the region data produced after the Flattener stage of [Metadata-Manager](https://github.com/DEIB-GECO/Metadata-Manager).


## Prerequisites:
* A directory (***source_dir***) containing the region data and metadata files for a dataset of interest. Such directory is created by [Metadata-Manager](https://github.com/DEIB-GECO/Metadata-Manager) after the Flattener stage.  
* A database connection where to load region data (***target_db***)
* A database table (***target_table***) where to load the region data files. The table must have a column for every region attribute of interest.

## Usage
1. Download this repository and move inside it.
2. Edit the database connection parameters according to your database configuration (lines 5-9 of *db_utils.py*). It is suggested to use the same database created by [Metadata-Manager](https://github.com/DEIB-GECO/Metadata-Manager) in order to make metadata and region data querable through a single connection.
3. (Optional) Edit lines 23-24 of *geco5_loader.py* to match the schema of ***target_table***. If the schema of ***target_table*** is a selection of the available GDM region attributes, then set:
   
   * *is_reduced_columns = True*
   * *reduced_columns = { indices of the GDM region attributes }*   
4. Launch *geco5_loader.py* with three arguments:

   1. /path/to/***source_dir*** (location of GDM dataset)
   2. ***target_db*** (the database where to load region data)
   3. ***target_table*** (the database table where to load region data)


## License
This software is released under the Apache License 2.0.
