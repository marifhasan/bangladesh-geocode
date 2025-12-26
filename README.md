Bangladesh GeoCode
==================

**Division**, **District**, **Upazila** and, **Union** level fully mapped MySQL Database. Available in two formats: consolidated single-table structure or separate tables for each level.

> All information, content and spelling has been taken from bangladesh.gov.bd, wikipedia.org, maps.google.com

#### Database Structure

**Option 1: Consolidated Single Table (Recommended)**

All location data in one `locations` table with hierarchical parent-child relationships. Import one file for complete geo information.

**Table Schema:**
* `id` - Primary key
* `name` - Location name in English
* `name_bn` - Location name in Bangla
* `type` - Location type (country, division, district, upazila, union)
* `parent_id` - Reference to parent location ID (for hierarchical structure)
* `lat` - Latitude (3 meter accuracy for district centers)
* `lon` - Longitude (3 meter accuracy for district centers)
* `url` - Government verified website address
* `created_at` - Timestamp
* `updated_at` - Timestamp

**Query Examples:**
* Get all divisions: `SELECT * FROM locations WHERE type = 'division'`
* Get districts of a division: `SELECT * FROM locations WHERE type = 'district' AND parent_id = {division_id}`
* Get complete hierarchy: Use `parent_id` to traverse up or down the location tree

**Option 2: Separate Tables (Legacy)**

Traditional approach with separate tables for each administrative level. Use JOIN queries to link data.

* **Divisions Table**
    * Division name in English
    * Division name in Bangla
    * Division's government verified website address
* **Districts Table** (mapped with Division)
    * District name in English
    * District name in Bangla
    * District Commissioner's (DC) office - latitude (3 meter accuracy)
    * District Commissioner's (DC) office - longitude (3 meter accuracy)
    * District's government verified website address
* **Upazilas Table** (mapped with District)
    * Upazila name in English
    * Upazila name in Bangla
    * Upazila's government verified website address
* **Unions Table** (mapped with Upazila)
    * Union name in English
    * Union name in Bangla
    * Union's government verified website address

#### Available Formats

**Consolidated Single Table:**
All formats in the `/locations` directory:
* SQL - `locations/locations.sql`
* CSV - `locations/locations.csv`
* JSON - `locations/locations.json`
* PHP Array - `locations/locations.php`
* XML - `locations/locations.xml`

**Separate Tables:**
Each administrative level has its own directory with all formats:
* Divisions - `divisions/` directory (SQL, CSV, JSON, PHP, XML)
* Districts - `districts/` directory (SQL, CSV, JSON, PHP, XML)
* Upazilas - `upazilas/` directory (SQL, CSV, JSON, PHP, XML)
* Unions - `unions/` directory (SQL, CSV, JSON, PHP, XML)

#### Upcoming columns
* Postal Code
* Area
* Population   

#### New Features
* GeoJSON data for every districts is available

> Please, create a pull request to add, update, or delete any records!   

#### Now Accepting - 
❤️ [Paypal Donation](https://www.paypal.me/nuhil)   

#### Contact
Feel free to find and contact me at [Nuhil.net](https://nuhil.net "Go To My Blog")
