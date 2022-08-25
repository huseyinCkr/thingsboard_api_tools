Not ready for prime time!  (Incomplete and undocumented, but what's here is useful and works.)

This code is utterly untested, but will get you pointed in the right direction.

    mothership_url = "http://www.wherever.org:8080"
    thingsboard_username = "who_are_you"
    thingsboard_password = "xyzzy"

    tbapi = TbApi(mothership_url, thingsboard_username, thingsboard_password)

    device = tbapi.get_device_by_name("device_name")

    latest_temp = tbapi.get_latest_telemetry(device, "temperature")
    all_humidity = tbapi.get_telemetry(device, "humidity")     # Lots more options on this method


STEP 1: build and install TbApi
-------------------------------
  cd thingsboard_api_tools
  
  python setup.py build     //will build the package underneath 'build/'
  
  python setup.py install   // will install the package

STEP 2: create sample app -> sample.py
--------------------------------------
  cd ..
  nano sample.py
  
  Sample Code:
  ------------
	from thingsboard_api_tools import TbApi
	mothership_url = "http://127.0.0.1:8080"
	thingsboard_username = "tenant@thingsboard.org"
	thingsboard_password = "tenant"

	tbapi = TbApi(mothership_url, thingsboard_username, thingsboard_password)

	latest_temp = tbapi.get_latest_telemetry("4f578fa0-22ef-11ed-b503-d7bb887165a6", "temperature")

	print(latest_temp.items())

	all_temp = tbapi.get_telemetry("4f578fa0-22ef-11ed-b503-d7bb887165a6", "temperature")

	print(all_temp.items())

   STEP 4: run python sample.py
   ----------
   OUTPUT:
   dict_items([('temperature', [{'ts': 1661356138897, 'value': '5269'}, 
   {'ts': 1661356108742, 'value': '31352'}, {'ts': 1661356078558, 'value': '28595'},
   {'ts': 1661356048371, 'value': '23872'}, {'ts': 1661356018212, 'value': '18321'}, 
   {'ts': 1661355988056, 'value': '31240'}, {'ts': 1661355957899, 'value': '30234'}, 
   ...
   {'ts': 1661351265014, 'value': '1051'}])])
