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





PART 2



LDM :

BOUTIQUE = (boutique_code VARCHAR(50), boutique_name VARCHAR(50), boutique_city VARCHAR(50), boutique_country VARCHAR(50), Boutique_prestige_tier_classification VARCHAR(50), boutique_phone VARCHAR(50));

ARTISAN = (Artisan_ID_ VARCHAR(50), Years_Experience INT, Artisan_First_Name_ VARCHAR(50), Artisan_Last_Name_ VARCHAR(50), Craft_Specialty_ VARCHAR(50), Hire_Date_ DATE, Workshop_Location VARCHAR(50));

CLIENT_VIP = (VIP_Number_ VARCHAR(50), Client_First_Name_ VARCHAR(50), Client_Last_Name_ VARCHAR(50), Client_Email_ VARCHAR(50), Client_Phone_ VARCHAR(50), Preferred_Language_ VARCHAR(50), Spend_Tier_ VARCHAR(50));

LIMITED_PRODUCT = (Product_Reference_ VARCHAR(50), Product_Name_ VARCHAR(100), Product_Category_ VARCHAR(50), Material_Description_ VARCHAR(50), Production_Limit_ VARCHAR(50), Catalog_Price_ DECIMAL(15,2));

BESPOKE_ORDER_ = (#VIP_Number_, Order_Sequential_Num_ VARCHAR(50), Order_Date_ VARCHAR(50), Estimated_Date_ VARCHAR(50), Final_Price_ VARCHAR(50), Production_Status_ VARCHAR(50), Client_Request_Notes_ VARCHAR(50), #Artisan_ID_, #boutique_code);

MENTOR = (#Artisan_ID_, Mentorship_Start_Date_ DATE, #Artisan_ID__1);

STOCK = (#boutique_code, #Product_Reference_, Stock_Quantity INT);

PURCHASE = (#VIP_Number_, #Product_Reference_, Purchase_Date DATE, Purchase_Quantity INT);



IV. Fourth Step : Inserting Data

Prompt:

"Provide the insertion queries used to populate the database, whose relational model is as follows:

BOUTIQUE(Boutique_Code, Boutique_Name, Boutique_City, Boutique_Country, Prestige_Tier, Boutique_Phone) Primary Key: Boutique_Code

ARTISAN(Artisan_ID, First_Name, Last_Name, Craft_Specialty, Hire_Date, Years_Experience, Workshop_Location, #Mentor_ID, Mentorship_Start_Date) Primary Key: Artisan_ID

CLIENT_VIP(VIP_Number, First_Name, Last_Name, Email, Phone, Preferred_Language, Spend_Tier) Primary Key: VIP_Number

LIMITED_PRODUCT(Product_Reference, Product_Name, Product_Category, Material_Description, Production_Limit, Catalog_Price) Primary Key: Product_Reference

BESPOKE_ORDER(#VIP_Number, Order_Sequential_Num, Order_Date, Estimated_Date, Final_Price, Production_Status, Client_Request_Notes, #Artisan_ID, #Boutique_Code) Primary Keys: VIP_Number, Order_Sequential_Num

STOCK(#Boutique_Code, #Product_Reference, Stock_Quantity) Primary Keys: Boutique_Code, Product_Reference

PURCHASE(#VIP_Number, #Product_Reference, Purchase_Date, Purchase_Quantity) Primary Keys: VIP_Number, Product_Reference, Purchase_Date


Primary keys correspond to IDs, unless otherwise specified (when it is a composite attribute).
Foreign keys are identified by # and have the same name as the primary keys to which they refer.

There must be: 5 rows for BOUTIQUE, 8 rows for ARTISAN (including at least 3 masters who have NULL for Mentor_ID, and 5 juniors who refer to those masters), 10 rows for CLIENT_VIP, 8 rows for LIMITED_PRODUCT, 15 rows for BESPOKE_ORDER, 15 rows for STOCK, and 20 rows for PURCHASE.

The data should reflect a high-end luxury fashion and haute couture brand (similar to Louis Vuitton or Hermès) with international boutiques, exquisite materials, and very wealthy clients of mixed international origins.

Foreign keys must refer to existing primary keys: provide the lines starting with filling in the tables in which there are no foreign keys, then the tables in which the foreign keys refer to primary keys in tables that have already been filled in. For the recursive ARTISAN table, ensure you insert the masters before the juniors.

The data must comply with the following validation constraints:

ALTER TABLE ARTISAN ADD CONSTRAINT chk_mentorship_date CHECK (Mentorship_Start_Date >= Hire_Date);

ALTER TABLE BESPOKE_ORDER ADD CONSTRAINT chk_order_dates CHECK (Estimated_Date >= Order_Date);

ALTER TABLE LIMITED_PRODUCT ADD CONSTRAINT chk_positive_price CHECK (Catalog_Price > 0);

ALTER TABLE LIMITED_PRODUCT ADD CONSTRAINT chk_positive_limit CHECK (Production_Limit > 0);

ALTER TABLE STOCK ADD CONSTRAINT chk_positive_stock CHECK (Stock_Quantity >= 0);

ALTER TABLE PURCHASE ADD CONSTRAINT chk_positive_purchase CHECK (Purchase_Quantity > 0);

ALTER TABLE BESPOKE_ORDER ADD CONSTRAINT chk_positive_bespoke_price CHECK (Final_Price >= 0);
Provide the set in the form of an SQL script ready to be executed."


V. Fifth step : querying the database

Usage scenario :
For our primary usage scenario, we imagine the database being used by the brand's Global Marketing Director and the Client Relationship Management team. Suppose the house is planning an ultra-exclusive runway show in Paris and needs to curate the perfect guest list. The marketing team will use the database to analyze VIP client purchasing behavior, specifically filtering for our top-tier Diamond clients to ensure our biggest spenders receive priority access. Because our clientele is international, the team will also extract preferred language data to send out highly personalized, localized invitations. Beyond just organizing the event, the team needs to track the overall popularity of our limited-edition products and check stock levels across our international boutiques. This way, if a VIP client wants to acquire a rare piece they saw on the runway, the marketing and sales teams already know exactly which boutiques have the inventory to fulfill that request immediately.
