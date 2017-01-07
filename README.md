# MacBook Pro Battery Life Test

This repository contains a simple test script to emulate a relatively heavy workload for battery life testing. It downloads a copy of [Drupal VM](https://www.drupalvm.com) and repeatedly builds and destroys a Virtual Machine running Drupal.

The script does the following, in a loop:

  1. Write a counter, timestamp and the battery percentage (as reported by `pmset`) to a results file.
  3. Run `vagrant up` to configure a VM running Drupal on a standard LAMP stack.
  5. Run `vagrant destroy -f` to destroy the VM.
  6. Wait 10s.
  7. Repeat.

To run the script, you should already have the latest versions of [Vagrant](https://www.vagrantup.com/downloads.html) and [VirtualBox](https://www.virtualbox.org/wiki/Downloads) installed.

## Usage

Download this project to your computer (either download through GitHub or clone it with Git).

  1. **Disable Sleep**: Go to System Preferences > Energy Saver, click on the 'Battery' tab, and drag the 'Turn display off after' slider all the way to 'Never' (alternatively, you could run `caffeinate` in a separate Terminal window).
  2. **Turn up brightness**: For consistency's sake, turn up your screen brightness all the way.
  3. **Quit all other Applications**: To make it a fair comparison. (I also make sure all my Macs are running identical software configurations using the [Mac Development Ansible Playbook](https://github.com/geerlingguy/mac-dev-playbook)).
  4. **Run Script**: Open Terminal, and cd into this project's directory. Run `./battery-test.sh`, and then walk away for a while.

After your Mac forces a sleep (when the battery has run out), plug it back in, then check the file that was stored in `results/` in the project directory.

## Results

Results are written to a date-and-timestamped file inside the `results` folder. This file is in CSV format, so you can open it in Excel, Numbers, Google Sheets, or any other CSV-compatible program and graph the results as needed.

## Author

This script was created by [Jeff Geerling](http://www.jeffgeerling.com) to run some more formal battery tests on the 2016 Retina MacBook Pro—both with and without Touch Bar—and to see if battery life and performance between the two models (under heavier load) was much different.