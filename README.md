## Configuration for my personal Kubenetes cluster running on a bunch of Raspberry Pi's.

#### For this configuration I used a number of resources, the first and probably the most used was the following YouTube [videos](https://www.youtube.com/watch?v=-MVkt2epGg4&list=PLThvbuXxyfhI6LudTDqajxkacclOdFrAr). The configuration within this repository assumes the setup of the clustered environment has been completed as shown within the YouTube tutorials.

#### To run the following, user a similar command to the following making sure you specify the ansible user

* `local-kubenetes $ ansible-playbook plays/base.yml --inventory inventory/hosts -u pi -k -vvv` - Run the base play as the `remote_user` pi and ask for the user's password