# ProjectDB_AISSA-BENHADDAD.Abdelkader_ISRAEL-Hillel
#prompt
"You work in the field of luxury fashion and haute couture. Your company is involved in the domain of designing, manufacturing, and selling high-end leather goods, bespoke jewelry, and exclusive ready-to-wear collections. It is a company such as Louis Vuitton, Hermès, or Dior.

We have collected data concerning: our international boutiques, our highly skilled artisans (including mentoring relationships between master and junior artisans), our VIP clientele profiles, the complex bespoke orders (which always involve a specific client, a dedicated boutique, and an assigned artisan), and the limited editions of our products. Take inspiration from the following websites and articles: the LVMH group corporate presentation (https://www.lvmh.com/group/) and general knowledge about Hermès bespoke services and craftsmanship.

Your company wants to apply MERISE to design an information system. You are responsible for the analysis part, i.e., gathering the company's requirements. It has called on a computer engineering student to carry out this project, and you must provide him with the necessary information so that he can then apply the following steps of database design and development himself.

First, establish the data business rules for your company in the form of a bulleted list. It must correspond to the information provided by someone who knows how the company works, but not how an information system is built.

Next, based on these rules, provide a raw data dictionary with the following columns, grouped in a table: meaning of the data, type, size in number of characters or digits. There should be between 25 and 35 data items. It is used to provide additional information about each data item (size and type) but without any assumptions about how the data will be modeled later.

Provide the business rules and the data dictionary."




#Business Rules

Part 1: Data Business Rules
Here are the operational rules for our High Fashion Maison, designed to structure our information system:


Our Boutiques & Network

We operate a network of international boutiques. Each boutique is identified by a unique code, a name, and its location (city and country).

Each boutique has a specific prestige tier (e.g., Flagship, Pop-up, Historical) and a main phone number.


Our Artisans & Transmission (Recursive Relationship)

Each artisan is identified by a unique employee ID. We record their first name, last name, craft specialty (e.g., Leatherworking, Gem-setting), and hire date.

Transmission of savoir-faire is key: A "Junior" artisan must be mentored by a "Master" artisan.

A "Master" can mentor several juniors, but a junior has only one active mentor at a time. This constitutes a strict internal hierarchy.


Our VIP Clientele (Strong Entity)

Our clients are exclusive members identified by a unique VIP membership number.

We maintain their personal details (first name, last name), contact information (email, phone), preferred language, and lifetime spending tier (e.g., Platinum, Diamond).


Bespoke Orders (Weak Entity)

"Bespoke" is our ultra-personalized service. To maintain client privacy and exclusivity, we do not use global order numbers.

Specific Rule: A bespoke order is identified by a sequential number internal to the client's file (e.g., Client X's 1st order, Client X's 2nd order). Therefore, an order cannot exist without being attached to a VIP Client.

Each order tracks a creation date, an estimated delivery date, a final negotiated price, and a production status.

An order is always managed by exactly one boutique and crafted by exactly one lead artisan.


Limited-Edition Products

We create rare products (handbags, watches) identified by a unique reference.

Each product has a name, a category, a material description, a catalog price, and a strict production limit (e.g., max 50 pieces worldwide).


#Data Dictionary

Meaning of the data,Type,Size (Chars/Digits)

BOUTIQUE,,
Boutique unique code,Alphanumeric,10
Boutique name,Alphanumeric,50
Boutique city location,Alphanumeric,50
Boutique country location,Alphanumeric,50
Boutique prestige tier,Alphanumeric,20
Boutique phone number,Alphanumeric,20

ARTISAN,,
Artisan employee ID,Alphanumeric,10
Artisan first name,Alphanumeric,50
Artisan last name,Alphanumeric,50
Craft specialty,Alphanumeric,40
Hire date,Date,10
Mentorship start date,Date,10

VIP CLIENT,,
VIP membership number,Alphanumeric,15
Client first name,Alphanumeric,50
Client last name,Alphanumeric,50
Client email address,Alphanumeric,100
Client phone number,Alphanumeric,20
Preferred language,Alphanumeric,20
Lifetime spend tier,Alphanumeric,30

LIMITED EDITION PRODUCT,,
Product reference code,Alphanumeric,15
Product name,Alphanumeric,100
Product category,Alphanumeric,30
Primary material description,Alphanumeric,200
Production limit (Max Qty),Numeric,4
Catalog price (Euros),Numeric,8

BESPOKE ORDER,,
"Order sequential number (e.g., 01, 02...)",Numeric,3
Order creation date,Date,10
Estimated delivery date,Date,10
Final negotiated price,Numeric,9
Production status,Alphanumeric,30
Special request description,Alphanumeric,500

<img width="1290" height="637" alt="image" src="https://github.com/user-attachments/assets/10996945-538b-478d-a2f8-dfbf300c972d" />
<img width="1290" height="637" alt="image" src="https://github.com/user-attachments/assets/10996945-538b-478d-a2f8-dfbf300c972d" />

