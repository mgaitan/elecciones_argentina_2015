Elecciones Argentina 2015
==========================

Dump de datos en formato CSV del programa http://www.resultados.gob.ar/inimesas.htm


¿Por qué?
---------

Los datos desagregado por mesa que proporciona la Justicia Electoral están empaquetados en una aplicación para Windows
utilizando una base de datos en formato Microsoft Access (.mdb) que es dificil de utilizar con otras aplicaciones.


Liberando los datos
---------------------

Los csv se extrajeron a través del software libre `mdbtools <http://mdbtools.sourceforge.net>`_ ::


    $ sudo apt-get install mdbtools

Instalar el programa con Wine y luego, utilizando IPython


.. code:: python

    In [1]: cd "~/.wine/drive_c/Program Files (x86)/Argentina 2015/DATOS"


    In [2]: !!mdb-tables ARGENTINA2015.mdb
    Out[2]: ['IndEle MesasCandidaturaConcejales MesasCandidaturaDProvinciales MesasCandidaturaGobernador MesasCandidaturaPNacionales MesasCandidaturaPRegionales MesasCandidaturaPresidente MesasCandidaturaSNacionales MesasCandidaturaSProvinciales MesasConcejales MesasDProvinciales MesasGobernador MesasPNacionales MesasPRegionales MesasPresidente MesasSNacionales MesasSublemaConcejales MesasSublemaDNacionales MesasSublemaDProvinciales MesasSublemaPNacionales MesasSublemaPRegionales MesasSublemaPresidente MesasSublemaSNacionales MesasSublemaSProvinciales NomAmbitos NomCandidatosPresidente NomElecciones NomMunicipios NomPartidos TotalCandidaturaConcejales TotalCandidaturaDNacionales TotalCandidaturaDProvinciales TotalCandidaturaPNacionales TotalCandidaturaPRegionales TotalCandidaturaPresidente TotalCandidaturaSNacionales TotalCandidaturaSProvinciales TotalConcejales TotalDNacionales TotalDProvinciales TotalPNacionales TotalPRegionales TotalPresidente TotalSNacionales TotalSProvinciales TotalSubLemaConcejales TotalSubLemaDProvinciales TotalSubLemaGobernador TotalSubLemaPNacionales TotalSubLemaPRegionales TotalSubLemaPresidente TotalSubLemaSNacionales TotalSubLemaSProvinciales MesasCandidaturaDNacionales MesasDNacionales MesasSProvinciales MesasSublemaGobernador NomCandidatosGobernador TotalCandidaturaGobernador TotalGobernador TotalSubLemaDNacionales ']

    In [3]: tables = _[0].split()

    In [4]: for table in tables:
       ...:     !mdb-export ARGENTINA2015.mdb {table} > {table}.csv
       ...:


Otras elecciones
----------------

- También están disponibles los datos de las `elecciones de 2013 <https://github.com/mgaitan/elecciones_argentina_2015>`_
