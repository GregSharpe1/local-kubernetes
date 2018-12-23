## Configuration for my personal Kubenetes cluster running on a bunch of Raspberry Pi's. Which are running the latest raspbian lite image as of December 23rd 2018 with ssh enabled and a static ip set from first boot. If you wish to find out how that was accomplished see [here](https://howchoo.com/g/ote0ywmzywj/how-to-enable-ssh-on-raspbian-without-a-screen) for enabling ssh on boot and [here](https://howtoraspberrypi.com/how-to-raspberry-pi-headless-setup/) for static ip on first boot.

#### For this configuration I used a number of resources, the first and probably the most used was the following YouTube [videos](https://www.youtube.com/watch?v=-MVkt2epGg4&list=PLThvbuXxyfhI6LudTDqajxkacclOdFrAr). The configuration within this repository assumes the setup of the clustered environment has been completed as shown within the YouTube tutorials.

#### To run the following, user a similar command to the following making sure you specify the ansible user

* `local-kubenetes $ ansible-playbook plays/base.yml --inventory inventory/hosts -u pi -k -vvv` - Run the base play as the `remote_user` pi and ask for the user's password the first time, the base play well remove the dependancy on sudo password for ease of deployment.

#### There is sensitive information containing passwords etc within the `inventory/group_vars/all.yml` for obvious reasons I don't want to display them, but they are required as part of this configuration. An example of the file is as follows

			---

			hostname_suffix: "pi-cluster"

			users_system:
			  - pi

			user_users:
			  - name: pi
			    state: present
			    password: "password generated using passlib python or [mkpasswd](https://serversforhackers.com/c/create-user-in-ansible)"
			    sudo: custom
			    sudo_custom:
			    - name: pi
			      nopasswd: yes
			      command_line: ALL
			    ssh_keys:
			      - key: example ssh public key