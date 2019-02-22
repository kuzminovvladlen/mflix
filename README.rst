=====
mflix
=====

This is a short guide on setting up the system and environment dependencies
required for the MFlix application to run.


Project Structure
-----------------

Everything you will implement is located in the ``mflix/db.py`` file, which
contains all database interfacing methods. The API will make calls to ``db.py``
to interact with MongoDB.

The unit tests in ``tests`` will test these database access methods directly,
without going through the API. The UI will run these methods in integration
tests, and therefore requires the full application to be running.

The API layer is fully implemented, as is the UI. If you need to run on a port
other than 5000, you can edit the ``index.html`` file in the build directory to
modify the value of **window.host**.

Please do not modify the API layer in any way, ``movies.py`` and ``user.py``
under the **mflix/api** directory. Doing so will most likely result in the
frontend application failing to validate some of the labs.


Python Library Dependencies
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Once the Python 3 environment is activated, we need to install our python
dependencies. These dependencies are defined in the ``requirements.txt`` file,
and can be installed with the following command:

.. code-block:: sh

  pip install -r requirements.txt

Importing Data
--------------

The ``mongorestore`` command necessary to import the data is located below. Copy
and paste the command, and replace ``<your-atlas-uri>`` with your Atlas SRV
string:

.. code-block:: sh

  # navigate to mflix-python directory
  cd mflix-python

  # import data into Atlas
  mongorestore --drop --gzip --uri <your-atlas-uri> data


Running the Application
-----------------------

In the ``mflix-python`` directory there are ``example.ini`` file.

Rename this file to ``.ini`` with the following command:

.. code-block:: sh

  mv example.ini .ini  # on Unix

Once the file has been renamed, open it, and enter your Atlas SRV connection
string as directed in the comment. This is the information the driver will use
to connect!

To start MFlix, run the following command:

.. code-block:: sh

  python run.py


And then point your browser to `http://localhost:5000/<http://localhost:5000/>`_.


Running the Unit Tests
----------------------

To run the unit tests for this course, you will use ``pytest``. Each course lab
contains a module of unit tests that you can call individually with a command
like the following:

.. code-block:: sh

  pytest -m LAB_UNIT_TEST_NAME

Each ticket will contain the command to run that ticket's specific unit tests.
