# cloud-cadavre-exquis-kubemaster

The exquisite corpse is a graphic game or collective writing invented by the surrealists, in particular Jacques Prévert and Yves Tanguy, around 1925.
The game consists in having several people compose a sentence, or a drawing, without any they cannot take into account the collaboration or previous collaborations.

This repository using the code from: [fteychene/cloud-cadavre-exquis](https://github.com/fteychene/cloud-cadavre-exquis)

## Installation on OVH Cloud:

### Allocating machines
You first need to allocate machines on OVH public cloud :
To do so, connect to your user page, then :
- Naviguate to Public Cloud 
- Navigaute to Instances
- Click on Create an instance
- Configure your server. We recommand going for at least B2-7, which has the minimal recommended specs for using the app.
- Create at least 2 instances, we recommend using 4.
- Take note of all your machines' IP.

### Configuring Ansible :
 - Edit the `inventory.ini` file :
    - On the first line, replace the master's IP with one of your machine, indicating the default user name, and indicate the path to the private key you used during allocation.
    - Do the same for all the other machines, creating or removing lines to match the number of instances you have.
    - For the k3s-master role, put the name of your first machine in the inventory
    - For the k3s-node role, put the name of all the others machines.

- Browse to `roles/deploy/tasks/main.yaml` :
  - On line 13, replace `dispatcher-domain` to your own domain.

### Running the script :
Make sure you have ansible package installed on your machine, then run `ansible-playground main.yaml`.

Let the script run, and you should be all set !

