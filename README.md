# grade-reaper

UWaterloo student, want to see what you [failed](http://ugradcalendar.uwaterloo.ca/page/uWaterloo-Grading-System) this term without using the usual [Quest](http://quest.uwaterloo.ca/) interface?

## Setup

### Dependencies

####Python Dependencies:

* [mechanize](http://wwwsearch.sourceforge.net/mechanize/): `pip install mechanize`
* [BeautifulSoup](http://www.crummy.com/software/BeautifulSoup/): `pip install BeautifulSoup`
* [argparse](https://code.google.com/p/argparse/): `pip install argparse`
* [requests](http://docs.python-requests.org/en/latest/): `pip install requests`
* [prettytable](http://code.google.com/p/prettytable/): `pip install prettytable`

Or install all dependencies at once with `pip install mechanize BeautifulSoup argparse requests prettytable`.

`pip` should be run as root.

####Submodule Dependencies:

* [scrape-quest](https://github.com/0/scrape-quest): `git submodule update --init` (NB. It has its own dependencies.)

This should be run in the repository folder.

### Configuration

Fill in as much Quest information as you feel comfortable at the top of `grades.py`. Whatever is missing can be provided on the command-line or will be requested interactively.

A free [Mailgun](https://mailgun.com) account is required to send the emails, and the information at the top of `grades.py` in the email configuration section should be filled out. Sandbox information and API Key can be found in the [control panel](https://mailgun.com/cp).

## Usage

`./grades.py --help`

### Interactive single run

`./grades.py`

Prompts for everything necessary to obtain some grades, and then displays said grades.

### Automated polling

`./grades.py --username a99bcdef --term 2 --loop --email`

Prompts for the password, and then loops, occasionally updating the term '2' grades, with an email being sent whenever anything interesting happens. Terminates when all grades become available.

To run the polling script in the background, use it in a `screen` session. By filling in the user details in `grades.py`, you can loop the script as follows:

`./grades.py --loop --email`