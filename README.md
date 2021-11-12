## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/grandedyb/DybraPortfolio/edit/main/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

<iframe frameborder="0" width="100%" height="500px" src="https://replit.com/@granded/airplaneowners?embed=true"></iframe>


### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
import sqlite3
from datetime import datetime
import csv

conn = sqlite3.connect('mydatabase.db')
cur = conn.cursor()
cur.execute('DROP TABLE IF EXISTS FAA_REGS')
cur.execute('''
CREATE TABLE "FAA_REGS"(
  "n_number" NUMBER,
  "serial_number" NUMBER,
  "mfr_mdl_code" NUMBER,
  "eng_mfr_mdl" NUMBER,
  "year_mgr" TEXT,
  "type_registrant" TEXT,
  "name" TEXT,
  "street" TEXT,
  "street2" TEXT,
  "city" TEXT,
  "state" TEXT,
  "zip_code" NUMBER,
  "region" TEXT,
  "county" TEXT,
  "country" TEXT,
  "last_action_date" DATE,
  "cert_issue_date" DATE,
  "certification" TEXT,
  "type_aircraft" TEXT,
  "type_engine" TEXT,
  "status_code" TEXT,
  "mode_s_code" TEXT,
  "fract_owner" TEXT,
  "air_worth_date" DATE,
  "other_name_1" TEXT,
  "other_name_2" TEXT,
  "other_name_3" TEXT,
  "other_name_4" TEXT,
  "other_name_5" TEXT,
  "expiration_date" DATE,
  "unique_id" NUMBER,
  "kit_mfr" TEXT,
  "kit_model" TEXT,
  "mode_s_code_hex" TEXT
)
''')

file = './FAA_REGS.txt'
with open(file) as csvDataFile:
    csvReader = csv.reader(csvDataFile, delimiter=',')
    next(csvReader)
    count = 0
    for row in csvReader:

        n_number = row[0]
        serial_number = row[1]
        mfr_mdl_code = row[2]
        eng_mfr_mdl = row[3]
        year_mgr = row[4]
        type_registrant = row[5]
        name = row[6]
        street = row[7]
        street2 = row[8]
        city = row[9]
        state = row[10]
        zip_code = row[11]
        region = row[12]
        county = row[13]
        country = row[14]
        last_action_date = row[15].lstrip().rstrip()
        cert_issue_date = row[16].lstrip().rstrip()
        certification = row[17]
        type_aircraft = row[18]
        type_engine = row[19]
        status_code = row[20]
        mode_s_code = row[21]
        fract_owner = row[22]
        air_worth_date = row[23].lstrip().rstrip()
        other_name_1 = row[24]
        other_name_2 = row[25]
        other_name_3 = row[26]
        other_name_4 = row[27]
        other_name_5 = row[28]
        expiration_date = row[29].lstrip().rstrip()
        unique_id = row[30]
        kit_mfr = row[31]
        kit_model = row[32]
        mode_s_code_hex = row[33]

        if certification == '1':
            certification = 'Standard'
        elif certification == '2':
            certification = 'Limited'
        elif certification == '3':
            certification = 'Restricted'
        elif certification == '4':
            certification = 'Experimental'
        elif certification == '5':
            certification = 'Provisional'
        elif certification == '6':
            certification = 'Multiple'
        elif certification == '7':
            certification = 'Primary'
        elif certification == '8':
            certification = 'Special Flight Permit'

        if cert_issue_date == '':
            cert_issue_date_rfmt = None
        else:
            cert_issue_date_rfmt = datetime.strptime(cert_issue_date,
                                                     '%Y%m%d').date()

        if last_action_date == '':
            last_action_date_rfmt = None
        else:
            last_action_date_rfmt = datetime.strptime(last_action_date,
                                                      '%Y%m%d').date()

        if air_worth_date == '':
            air_worth_date_rfmt = None
        else:
            air_worth_date_rfmt = datetime.strptime(air_worth_date,
                                                    '%Y%m%d').date()

        if expiration_date == '':
            expiration_date_rfmt = None
        else:
            expiration_date_rfmt = datetime.strptime(expiration_date,
                                                     '%Y%m%d').date()

        if status_code == 'V':
            status_code = 'Valid Registration'
        elif status_code == '1':
            status_code = 'Triennial Aircraft Registration form was returned by the Post Office as undeliverable'
        elif status_code == '25':
            status_code = 'First Notice for Registration Renewal'

        if type_registrant == '1':
            type_registrant = 'Individual'
        elif type_registrant == '2':
            type_registrant = 'Partnership'
        elif type_registrant == '3':
            type_registrant = 'Corporation'
        elif type_registrant == '4':
            type_registrant = 'Co-Owned'
        elif type_registrant == '5':
            type_registrant = 'Government'
        elif type_registrant == '6':
            type_registrant = 'LLC'
        elif type_registrant == '7':
            type_registrant = 'Non Citizen Corporation'
        elif type_registrant == '8':
            type_registrant = 'Non Citizen Co-Owned'

        if region == '1':
            region = 'Eastern'
        elif region == '2':
            region = 'Southwestern'
        elif region == '3':
            region = 'Central'
        elif region == '4':
            region = 'Western-Pacific'
        elif region == '5':
            region = 'Alaskan'
        elif region == '7':
            region = 'Southern'
        elif region == '8':
            region = 'European'
        elif region == 'C':
            region = 'Great Lakes'
        elif region == 'E':
            region = 'New England'
        elif region == 'S':
            region = 'Northwest Mountain'

        if type_engine == '0':
            type_engine = 'None'
        if type_engine == '1':
            type_engine = 'Reciprocating'
        elif type_engine == '2':
            type_engine = 'Turbo-prop'
        elif type_engine == '3':
            type_engine = 'Turbo-shaft'
        elif type_engine == '4':
            type_engine = 'Turbo-jet'
        elif type_engine == '5':
            type_engine = 'Turbo-fan'
        elif type_engine == '6':
            type_engine = 'Ramjet'
        elif type_engine == '7':
            type_engine = '2 Cycle'
        elif type_engine == '8':
            type_engine = '4 Cyle'
        elif type_engine == '9':
            type_engine = 'Unknown'
        elif type_engine == '10':
            type_engine = 'Electric'
        elif type_engine == '11':
            type_engine = 'Rotary'

        if type_aircraft == '1':
            type_aircraft = 'Glider'
        elif type_aircraft == '2':
            type_aircraft = 'Baloon'
        elif type_aircraft == '3':
            type_aircraft = 'Blimp/Dirigible'
        elif type_aircraft == '4':
            type_aircraft = 'Fixed wing single engine'
        elif type_aircraft == '5':
            type_aircraft = 'Fixed wing multi engine'
        elif type_aircraft == '6':
            type_aircraft = 'Rotorcraft'
        elif type_aircraft == '7':
            type_aircraft = 'Weight-shift-control'
        elif type_aircraft == '8':
            type_aircraft = 'Powered Parachute'
        elif type_aircraft == '9':
            type_aircraft = 'Gyroplane'
        elif type_aircraft == 'H':
            type_aircraft = 'Hybrid Lift'
        elif type_aircraft == 'O':
            type_aircraft = 'Other'

        if count > 15:
            break
        count += 1

        cur.execute(
            '''INSERT INTO FAA_REGS(n_number,serial_number,mfr_mdl_code,eng_mfr_mdl, year_mgr, type_registrant,name,street,street2,city,state,zip_code,
    region,county,country,last_action_date,cert_issue_date, certification,
    type_aircraft,type_engine,status_code,mode_s_code,fract_owner,air_worth_date,
    other_name_1,other_name_2,other_name_3,other_name_4,other_name_5,expiration_date,
    unique_id,kit_mfr,kit_model,mode_s_code_hex)
    VALUES (?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?)''',
            (n_number, serial_number, mfr_mdl_code, eng_mfr_mdl, year_mgr,
             type_registrant, name, street, street2, city, state, zip_code,
             region, county, country, last_action_date_rfmt,
             cert_issue_date_rfmt, certification, type_aircraft, type_engine,
             status_code, mode_s_code, fract_owner, air_worth_date_rfmt,
             other_name_1, other_name_2, other_name_3, other_name_4,
             other_name_5, expiration_date, unique_id, kit_mfr, kit_model,
             mode_s_code_hex))
        conn.commit()

        cur.execute("SELECT * FROM FAA_REGS")
        result = cur.fetchall()
        for i in result:
            print(i)

```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/grandedyb/DybraPortfolio/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
