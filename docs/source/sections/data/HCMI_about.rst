*************
HCMI Data Set
*************

About the Human Cancer Models Initiative
----------------------------------------

The `Human Cancer Models Initiative <https://ocg.cancer.gov/programs/HCMI>`_ (HCMI) is a collaborative international consortium that is generating novel, next-generation, tumor-derived culture models annotated with genomic and clinical data. The collaborating institutions are the `National Cancer Institute <https://www.cancer.gov/>`_ (NCI), `Cancer Research UK <https://www.cancerresearchuk.org/funding-for-researchers/how-we-deliver-research/our-research-partnerships/human-cancer-models-initiative>`_ (CRUK), `Wellcome Sanger Institute <https://www.sanger.ac.uk/science/collaboration/human-cancer-model-initiative-hcmi>`_ (WSI), and foundation `Hubrecht Organoid Technology <https://hub4organoids.eu/>`_ (HUB). The four `Cancer Model Development Centers <https://ocg.cancer.gov/programs/hcmi/nci-cancer-model-development>`_ (CMDCs), which are supported by the NCI as part of the HCMI, are Broad Institute of MIT and Harvard (BROAD), Cold Spring Harbor Laboratory (CSHL), Stanford University, and Weill Cornell Medical College.

About the Human Cancer Models Initiative Data
----------------------------------------------

HCMI data consists of 23 cases with over 450 phenotyped subjects with whole-exome sequencing, RNA sequencing, and whole-genome sequencing data. The NCI GDC houses all the clinical, biospecimen, and molecular characterization data with over 460 VCF, 261 BAM, 123 TXT, 57 TSV, and 23 BRC XML files. The Project ID in the GDC Data Portal is `HCMI-CMDC <https://portal.gdc.cancer.gov/projects/HCMI-CMDC>`_.

For more information on the HCMI data, please refer to these sites:

- `NCI Cancer Model Development <https://ocg.cancer.gov/programs/hcmi/nci-cancer-model-development>`_
- `dbGaP site <https://www.ncbi.nlm.nih.gov/projects/gap/cgi-bin/study.cgi?study_id=phs001486.v2.p2>`_
- `GDC Data Portal <https://portal.gdc.cancer.gov/repository?facetTab=cases&filters=%7B%22op%22%3A%22and%22%2C%22content%22%3A%5B%7B%22op%22%3A%22in%22%2C%22content%22%3A%7B%22field%22%3A%22cases.project.program.name%22%2C%22value%22%3A%5B%22HCMI%22%5D%7D%7D%5D%7D&searchTableTab=files>`_

Accessing the Human Cancer Models Initiative Data on the Cloud
---------------------------------------------------------------

Besides accessing the files on the GDC Data Portal, you can also access them from the GDC Google Cloud Storage Bucket, which means that you don’t need to download them to perform analysis. ISB-CGC stores the cloud file locations in tables in the ``isb-cgc.GDC_metadata`` data set in BigQuery.

- To access these metadata files, go to the Google BigQuery console.
- Perform SQL queries to find the HCMI files. Here is an example:

.. code-block:: sql

  SELECT active.*, file_gdc_url
  FROM `isb-cgc.GDC_metadata.rel22_fileData_active` as active, `isb-cgc.GDC_metadata.rel22_GDCfileID_to_GCSurl` as GCSurl
  WHERE program_name = 'HCMI'
  AND active.file_gdc_id = GCSurl.file_gdc_id
