# RC Reviews Plugin

#### Prerequisite:
The following credentials are needed in order to use the plugin.
* clientID
* clientSecret
* agencyID

---

#### Installation:
Install the plugin via composer.

    composer require mattneal/rcreviews-plugin

---

#### Setup:
There are two ways to setup the credentials:
* Add the credentials manually to the plugin settings on backend.
* Add as environment variables to the .env file.

##### Setup: Add via Plugin Settings
Please see steps below in order to set the credentials.
* Access the admin dashboard.
* On the sidebar menu, navigate to RC Reviews > Settings.
* Set the Client ID, Client Secret and Agent ID.
* Click the Save Changes button in order to generate the Access Token.
* Connection Status will display as Success if the credentials are correct.

##### Setup: Add as Environment Variables
We strongly advise to add the credentials to the .env file.  Add the following environment variables to the .env file.

    REA_CLIENT_ID
    REA_CLIENT_SECRET
    REA_AGENCY_ID

Add the following configs to the application.php file.

    Config::define( 'REA_CLIENT_ID', env( 'REA_CLIENT_ID' ) );
    Config::define( 'REA_CLIENT_SECRET', env( 'REA_CLIENT_SECRET' ) );
    Config::define( 'REA_AGENCY_ID', env( 'REA_AGENCY_ID' ) );

##### Setup: Custom Post Type Slug
The default custom post type slug used in the plugin is `rcreviews`. However, there are instances where you need to merge existing reviews from another post type, please steps below.

There are two ways to configure the custom post type slug.
* Set the slug to the plugin settings on backend under Custom Post Type Slug field.
* Set as environment variables to the .env files, variable name used is `REA_POST_TYPE_SLUG`.

Note that steps are the same with configuring the credentials. Changing custom post type slug later on will result moving the reviews to the new post type and only the reviews pulled from REA are moved.

---

#### Fetching Reviews
Please see steps below in order to sync reviews from REA to website.
* Access the admin dashboard.
* On the sidebar menu, navigate to RC Reviews.
* Click the Sync Reviews button to start with the sync.
* Note that while the reviews are being processed, please do not close the browser window.
* Wait until the progress bar is complete.
* On the sidebar menu, navigate to Reviews to view the list.

---

#### Emptying Reviews
There are instances where you accidentally merge the reviews to incorrect post type slug, in order to revert back the changes by deleting the synced reviews, please see steps below.
* Access the admin dashboard.
* On the sidebar menu, navigate to RC Reviews.
* Click the Empty Reviews button to start with the deletion.
* Note that while the reviews are being processed, please do not close the browser window.
* Wait until the progress bar is complete.

Note that when emptying the reviews, only the ones pulled from REA are removed.

---

#### Displaying Reviews
Reviews can be displayed using the [rcreviews] shortcode.

Review widget can be filtered by using the attributes below.
* max_reviews
* shown_reviews
* min_stars
* agent_id
* agent_name
* view
* listing_type

* max_reviews (integer) - Set the total number of reviews listed in the widget.
* shown_reviews (integer) - Set the number of shown reviews before the other reviews are hidden by collapse button.
* min_stars (integer) - Set the minimum star rating of the reviews.
* agent_id (string) - Use to filter the reviews by agent ID (from REA), need to assign the agent ID to the agent in order to use.
* agent_name (string) - Use to filter the reviews by agent name (should match the name from REA)
* view (string) - Setting the value to `unstyled` will remove the existing classes from the elements.
* listing_type (agent, agency) - Setting the value to `agency` will add the agenct details.

Review widget can be styled and customized by using the class attributes below.
* class_section
* class_container
* class_row
* class_article
* class_card
* class_inner_row
* class_rating
* class_rating_stars
* class_rating_number
* class_badge
* class_title
* class_date
* class_content
* class_agent
* class_agent_img-wrapper
* class_agent_img
* class_agent_name
* class_bin_wrapper
* class_btn
* class_no_results

Default classes used is based on Bootstrap, setting the `view` attribute to `unstyled` will remove pre-added classes .