templates: services packages kernel_modules permissions umasks sysctls

SHARED_DIR=../../../../../shared/oval/templates

services:
	${SHARED_DIR}/create_services_disabled.py services_disabled.csv
	${SHARED_DIR}/create_services_enabled.py services_enabled.csv

packages:
	./create_package_installed.py packages_installed.csv
	${SHARED_DIR}/create_package_removed.py packages_removed.csv

kernel_modules:
	${SHARED_DIR}/create_kernel_modules_disabled.py kernel_modules_disabled.csv

permissions:
	${SHARED_DIR}/create_permission_checks.py file_dir_permissions.csv

umasks:
	./create_umask_checks.py file_umask_checks.csv

sysctls:
	${SHARED_DIR}/create_sysctl_checks.py sysctl_values.csv
	
compare:
	diff output/ ../ | grep -v "Only in ../"

copy:
	cp output/*.xml ../
	cp output/*.sh ../../fixes/bash/

find-untemplated: templates
	./find_untemplated.py

clean:
	rm -f output/*.xml
	rm -f output/*.sh
