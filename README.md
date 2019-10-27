# spira
Ansible Tower script to pull inventory and configuration from Netbox

Augmented from [https://github.com/AAbouZaid/netbox-as-ansible-inventory](https://github.com/AAbouZaid/netbox-as-ansible-inventory) to allow for the pulling in of Configuration Context from Netbox.

place file netbox.yml on Docker container awx_task

`docker cp netbox.yml awx_task:/home/awx/netbox.yml`

create a dynamic inventory script in AWX:

1. Click on Inventory Scripts from menu
2. Click "Create new script" button
3. Give script a name
4. Paste in the netbox.py script in "Custom Script" box and save
5. Click on Inventory from menu
6. Click green button and select Create Inventory
7. Fill out necessary fields and save
8. Click the Sources tab
9. Click the green button
10. Assign a name to the dynamic inventory and select "Custom Script" from sources
11. Ensure your script created in step shows up under Custom Inventory Script field, change if needed
12. Under the Environmentals section, enter `NETBOX_CONFIG_FILE: /home/awx/netbox.yml` underneath the three `---` line
13. Select Update Options that align with your needs, I select all three (Update Options, Overwrite Variables, Update on Launch) and save
14. Click on Inventory from menu again
15. Select your dynamic inventory
16. Select Sources tab again
17. Look for a icon that shows two arrows chasing each other in a circle. click it to run your script