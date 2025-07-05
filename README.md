# product-inflation-tracker
product-inflation-tracker

<table>
<tr>
<td style="width 20%">
<img src="https://raw.githubusercontent.com/Eb43/eb43.github.io/refs/heads/main/monkey-writer-coder-small.jpg" alt="" style="height: 100px; width: 100px; object-fit: contain; object-position: 1% 1%"/>
</td>
<td>
<p style="font-size: 90%;">Eugen Barilyuk</p>
<p style="font-size: 90%;">Published: 6 July 2025</p>
<p style="font-size: 120%;"><a href="https://eb43.github.io/portfolio-page.html">←🏠 Back to <i><b>eb43.github.io</b></i> articles list</a></p>
<td>
</tr>
</table>


  
  <!-- <img src="https://raw.githubusercontent.com/Eb43/eb43.github.io/refs/heads/main/images/fast-charging-technologies-in-detail/slow-phone-charger.jpg" alt="" style="height: auto; width: 600px; object-fit: contain; object-position: 1% 1%; box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);"/>

<a href=".html" rel="nofollow"></a>

<details>
  <summary><i style="font-size: 100%; color: brown"><u>Click to unfold the rest of DIV</u></i></summary>

</details>
-->

<!--
<div style="background-color:#ffd938; border-radius: 8px; padding: 15px; overflow: hidden; margin: 0 auto; width: 500px; text-align:center; white-space: pre-wrap;">
<p style=" color: #111; width: 400px; text-transform: uppercase; text-align:center;  "><u>Nota Bene:</u> <br><b>Android without Google Play Store consumers view as not fully functional Android.</b></p>
<br>
<p></p>

</div>

-->

<h1>Produce Inflation Tracker vs. HTML Madness: A Journey Through the Chaotic Web Layouts of Grocery Websites</h1>
<div style="background-color:#1111; border-radius: 8px; padding: 15px; overflow: hidden; margin: 0 auto; width: 800px; text-align:center; white-space: pre-wrap;">
<p style=" width: 800px; text-transform: uppercase; text-align:center;  "><i>Before you begin reading - a note:</i> this is not a tech article. This is a survival log. A descent into the uncanny valley of e-commerce HTML. A tale of optimism murdered by CSS. A chronicle of how the simple act of wanting to know how much bread costs turned into a digital psychodrama. If you thought building a price tracker in 2025 is easy, you must get rid of your hallucinations and hope.</p>
</div>

<p>One summer day I was listening to a news piece on global economy, and noticed that I was nodding internally when the host started talking about inflation. While inflation is absolutely artificial (excessive money do not drop from the sky, they are printed by the government to cover its overspending), for ordinary people inflation is like a forest fire, which turns their finances into nothing.</p>

<p>The most interesting part of inflation is that while it is nationwide, every person has individual inflation. So, when a central bank states the inflation as 3% what does it mean? It means nothing for everyday life because each product has its own inflation rate. Bread prices may be inflating with a speed of 5% per year, car prices may be inflating with a speed of 1% per year. On average this gives 3% inflation. But you buy a car once in several years, and you buy bread every several days. Therefore, you will feel inflation close to 5%.</p>

<p>Knowing that official inflation level is as useful as a comb for a bald man, I got curious what a real inflation is for products consumed every day. Immediately I googled this only to find that searching "product inflation tracker" gives shady results of official inflation level, some useless indexes (like Big Mac Index) or calculators that want a user to provide the information on inflation level.</p>

<img src="https://raw.githubusercontent.com/Eb43/eb43.github.io/refs/heads/main/images/product-inflation-tracker-story-of-development/truflation.jpg" alt="" style="height: auto; width: 600px; object-fit: contain; object-position: 1% 1%; box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);"/>

<p>Immediately an idea sprawled: grocery stores exist, and they provide prices for products. Simply visit a store today, tommorrow, and after tommorrow, write down the price, and calculate how the price changed.</p>
<p>How hard can it be, right? Reality says - wrong!</p>

<h2>Simple idea of collecting data from website</h2>

<p>On the first glance, the task was an easy peasy one. We simply need to track product's page in a store and grab its price. Having the table of price and date the price was collected makes it easy to calculate inflation rate, build a nice visual chart, and do any other fancy stuff for data analysis.</p>
<p>Since a product may disappear from sale, it was decided not to track a particular product, but to track the cheapest product in its category. For example, cheapest bread. This makes sense, as people will continue buying bread anyways. It's the price that matters, not brand and product name.</p>

<p>Having established basics, an approach emerged:</p>
<ul>
  <li>Navigate to grocery store's website</li>
  <li>Search for a product that has to be tracked</li>
  <li>Sort the search result by price to get the cheapest product</li>
  <li>Nicely ask AI to help writing software code that grabs product title and price of the first product on the page. Since results are sorted starting cheapest one, the first product on page will have the lowest price</li>
  <li>Collect a database of price changes, calculate real inflation, show fancy charts</li>
  <li>Add more products for tracking, more stores, grab a beer and enjoy results</li>
</ul>  

<p>And that opened hell of HTML layouts.</p>

<div style=" border-radius: 8px; padding: 15px 15px 15px 15px; overflow: hidden; margin: 0 auto; width: 600px; text-align:center; box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);">
<iframe width="600" height="350" src="https://www.youtube.com/embed/KRBXW8Jw5Fc?si=MxQFRLef9ZWxchgk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

<h2>Who knew stores treat price tags like government secrets? Not me</h2>

<p>At first, the plan was honest and civilized: use the good old <i>BeautifulSoup</i> - a Python library as gentle and friendly as its name. I fed it some HTML from the first store, and it dutifully fetched the price like a golden retriever bringing a stick. Success! This is going to be easy, I thought. A classic setup:</p>

<p>At that point, my noble produce inflation tracker quietly died. Not with a bang, but with a CAPTCHA. Almost every store now demands you to prove you're human - simply for the honor of reading the price tag of a loaf of bread. It’s as if prices are state secrets, and shoppers are undercover agents. You just want to know how much eggs cost, and suddenly you're solving puzzles for an algorithm that doesn’t believe in your existence.</p>

<p>Having next store in the tracker’s list returned empty soup full of nothing except CAPTCHA wall, I escalated. AI has advised to bring out the big guns: Firefox, a real browser with a real user profile, controlled by Selenium. Driven by code, grocery stores opened their pages for a proper citizen of the Internet. </p>
<pre>
def fetch_page_selenium(url):
    firefox_options = FirefoxOptions()
    firefox_options.binary_location = r"d:\...firefox.exe"
    firefox_options.add_argument('--profile')
    firefox_options.add_argument(r'd:\...\firefox-for-selenium')
    firefox_options.set_preference("javascript.enabled", True)
    firefox_options.set_preference("general.useragent.override", 
        "Mozilla/5.0 ... Firefox/115.0")
    ...
    driver.get(url)
    driver.execute_script("Object.defineProperty(navigator, 'webdriver', {get: () => undefined})")
    ...
</pre>

<p>I impersonated Firefox 115.0 on Windows 10, disabled <code>navigator.webdriver</code>, accepted insecure TLS certificates, and pretended to be less secure than I actually am - all to read the price of loaf of bread. Meanwhile, real humans browse the same site with dozen of tabs open and two ad blockers, and still get through fine. Irony?</p>

<p>But it didn’t matter. Pages would load normally, well, mostly of times. A very real human behind this code and its AI helper, have to think more on how to disguise the code in layers of fake humanity, just to convince another machine that he's not a machine.</p>

<p>In the meanwhile, first set of data was carefully placed into database of the inflationtracker.</p>

<h2>Webscraping dreams crushed through duplicated CSS selector</h2>

<p>Having almost won the bot check battle, an HTML layout nightmare arose.</p>
<p>When I tried to remember any supermarket chain, a Walmart brand popped in my head. Absolute and pure random, but it already highlighted that this project will make me sweat.</p>
<p>I started from googling Walmart's website, got walmart.com, and immediately stumbled upon the question: for which country is this page? Walmart does not highlight (or I'm blind enough to see) the country. Prices have $ sign, units of measurements are imperial. I assumed that I was in a Walmart USA. But actually, by this day I don't know for which country the page is designated.</p>
<p>Anyway, I navigate to <i>https://www.walmart.com/search?q=bread&sort=price_low</i> and locate the HTML tags with product title and product price. That immediately gave a major headache.</p>
<p>You see, the tools for webscraping search the webpage by CSS selectors. For example, <i>data-automation-id="product-price"</i>. This selector is from Walmart's page, and you may assume it contains product price. And you will be right, but actually wrong (by the way, only now, while writing this article, I have actually noticed that this DIV contains price).</p> 

<pre style="background-color: rgba(211, 211, 211, 0.5); border-radius: 8px; padding: 15px; overflow: hidden; margin: 0 auto;  text-align:left; white-space: pre-wrap;">
&lt;div data-automation-id=&quot;product-price&quot; class=&quot;flex flex-wrap justify-start items-center lh-title mb1&quot;&gt;
   &lt;div class=&quot;mr1 mr2-xl b black lh-solid f5 f4-l&quot; aria-hidden=&quot;true&quot;&gt;&lt;span class=&quot;f3&quot;&gt;&lt;/span&gt;
      &lt;span class=&quot;f6 f5-l&quot; style=&quot;vertical-align:0.65ex;margin-right:2px&quot;&gt;$&lt;/span&gt;
      &lt;span class=&quot;f2&quot;&gt;1&lt;/span&gt;&lt;span class=&quot;f6 f5-l&quot; style=&quot;vertical-align:0.75ex&quot;&gt;82&lt;/span&gt;
    &lt;/div&gt;
&lt;/div&gt;
</pre>

<p>I have spotted that the price is provided outside of this DIV block in a <i>span</i> tag. Not a problem, use its <i>span class="w_iUH7"</i> selector! But who knew that exactly this selector is used for a product title:</p>

<pre style="background-color: rgba(211, 211, 211, 0.5); border-radius: 8px; padding: 15px; overflow: hidden; margin: 0 auto;  text-align:left; white-space: pre-wrap;">
<i>&lt;span class="w_iUH7"&gt;Freshness Guaranteed Garlic Herb French Bread, 14 oz&lt;!-- --&gt; &lt;/span&gt;</i>
<i>&lt;span class="w_iUH7"&gt;current price $1.82&lt;/span&gt;</i>
</pre>

<p>This resulted in a code that copied product title as product price.</p>

<img src="https://raw.githubusercontent.com/Eb43/eb43.github.io/refs/heads/main/images/product-inflation-tracker-story-of-development/walmart-repeating-title-as-price.jpg" alt="" style="height: auto; width: 500px; object-fit: contain; object-position: 1% 1%"/>

<p>After some talking to an AI, an updated code emerged that extracted data fields correctly. Hooray?</p>

<h2>CSS selectors with variable content</h2>

<p>After taming the chaos of duplicated CSS selectors - where both the product title and price were parsed as one - I thought I’d earned some peace. Wrong. The moment I exhaled, I fell straight into the next trap of HTML chaos: CSS selectors with unique content per item:</p>

<pre style="background-color: rgba(211, 211, 211, 0.5); border-radius: 8px; padding: 15px; overflow: hidden; margin: 0 auto;  text-align:left; white-space: pre-wrap;">
&lt;p class="chakra-text css-1ecdp9w" data-testid="product-brand"&gt;ACE&lt;/p&gt;&lt;h3 class="chakra-heading css-6qrhwc" id="21616092_EA" data-testid="product-title"&gt;Classic White Bistro&lt;/h3&gt;&lt;p class="chakra-text css-1yftjin" data-testid="product-package-size"&gt;595 g, $0.76/100g&lt;/p&gt;
</pre>

<p>At first glance, this HTML looks like a clean layout that is easy to fetch and parse. Then you realize: those class names like <code>id="21616092_EA"</code> are not stable. Every product had its own unique ID embedded.</p>

<p>Needless to say, my naive, hand-crafted, splintery script - forged lovingly with AI and blind optimism - had no idea how to navigate this mess. It broke faster than a politician’s promise under scrutiny.</p>

<p>So back I went back to negotiations with the artificial intelligence. This time, with a new agenda: teach the parser that some CSS selectors are variable. We, mostly AI, rewired the logic to work with variable attributes.</p>

<p>Code started to reliably fetch data from HTML layouts that have variable selectors, giving a faint hope that tomorrow, the HTML won't mutate... fast enough for the code to break.</p>

<h2>Product price split over multiple nested HTML tags</h2>

<p>Ok, now we're rocking the data collection, time to add another store. The code works flawlessly, scraping the next store should cause no problems.</p>

<p>And yes, there were no problems with grabbing a product title in this store. But price grabbing failed with a simple reason: website designer decided to make HTML layout with nested tags.</p>

<pre style="background-color: rgba(211, 211, 211, 0.5); border-radius: 8px; padding: 15px; overflow: hidden; margin: 0 auto;  text-align:left; white-space: pre-wrap;">
&lt;div class="catalog-item__product-price product-price product-price--weight "&gt;
  &lt;data class="product-price__top"&gt;
    &lt;span&gt;20&lt;span class="product-price__coin"&gt;90&lt;/span&gt;&lt;/span&gt; 
  &lt;/data&gt;
&lt;/div&gt;
</pre>

<p>This nested design then appeared again much later in HTML layout of another store that definitely was not connected with the previous one, as it was from another country almost 1500 kilometers apart. Moreover, this store had more severe HTML tag nesting, causing significant data duplication.</p>

<pre style="background-color: rgba(211, 211, 211, 0.5); border-radius: 8px; padding: 15px; overflow: hidden; margin: 0 auto;  text-align:left; white-space: pre-wrap;">
&lt;div data-testid="product-block-supplementary-price-2" class="sc-dqia0p-0 fLKnrn"&gt;250 g&lt;/div&gt;•&lt;div data-testid="product-block-price-per-unit" type="normal" class="sc-dqia0p-3 kGnDnm"&gt;1 kg = 91,60 Kč&lt;/div&gt;&lt;/div&gt;&lt;/div&gt;&lt;/div&gt;&lt;div data-testid="product-tile-footer" class="sc-y4jrw3-18 lnBzvN"&gt;&lt;div class="sc-y4jrw3-22 bZlgEg"&gt;&lt;div class="sc-y4jrw3-23 SlJTS"&gt;&lt;div class="sc-y4jrw3-27 eUiuhf"&gt;&lt;div data-stellar="st-web-price" data-testid="product-block-price" class="sc-dqia0p-2 bFXgow"&gt;&lt;div class="sc-dqia0p-8 kyoGRo"&gt;&lt;/div&gt;&lt;div class="sc-dqia0p-9 dsNELN"&gt;22&lt;/div&gt;&lt;sup class="sc-dqia0p-10 fjOrrj"&gt;90 &lt;/sup&gt;&lt;div class="sc-dqia0p-8 kyoGRo"&gt;Kč&lt;/div&gt;
</pre>

<p>The result was duplication of data, which looked like this respectively:</p>

<pre  style="background-color: rgba(211, 211, 211, 0.5); border-radius: 8px; padding: 15px; overflow: hidden; margin: 0 auto;  text-align:left; white-space: pre-wrap;">Full price: 20.90грн/шт 20.90грн/шт відділень 90 грн/шт /шт</pre>

<p>and</p>

<pre  style="background-color: rgba(211, 211, 211, 0.5); border-radius: 8px; padding: 15px; overflow: hidden; margin: 0 auto;  text-align:left; white-space: pre-wrap;">Full title: Albert Toustový chléb světlý, balený 250 g•1 kg = 91,60 Kč 250 g•1 kg = 91,60 Kč 250 g•1 kg = 91,60 Kč 250 g 1 kg = 91,60 Kč</pre>

<p>Ok, another round of negotiations with the AI, and then one more, and one more. Several days after, the correctly working code with improved <code>check_attributes_match()</code> and <code>extract_data_from_template()</code> complex functions were produced.</p>

<details>
  <summary><i style="font-size: 100%; color: brown"><u>Click to unfold the code</u></i></summary>
<pre>
def extract_data_from_template(template_lines, page_html):
    """Extract data from page using template"""
    template_html = '\n'.join(template_lines)
    #print(f"Template HTML: {template_html}")
    
    # Fix malformed template HTML - if it starts with attributes, add opening tag
    if template_html.strip().startswith('class=') or template_html.strip().startswith('data-'):
        template_html = '<a ' + template_html
    
    template_soup = BeautifulSoup(template_html, 'html.parser')
    page_soup = BeautifulSoup(page_html, 'html.parser')
    
    extracted_parts = []
    processed_elements = []
    
    # Process each template element that contains FFF
    for template_element in template_soup.find_all():
        if 'FFF' not in template_element.decode():
            continue
            
        #print(f"Processing template: {template_element}")
        
        # Find matching element in page
        matching_element = find_matching_element(page_soup, template_element)
        
        if matching_element:
            # Skip if we already processed this element or its parent/child
            skip_element = False
            for processed in processed_elements:
                # Skip if same element
                if matching_element == processed:
                    skip_element = True
                    break
                # Skip if this element is inside a processed element
                if matching_element in processed.descendants:
                    skip_element = True
                    break
                # Skip if a processed element is inside this element
                if processed in matching_element.descendants:
                    skip_element = True
                    break
            
            if skip_element:
                #print("Skipping - element already processed or related")
                continue
            
            # Extract text based on template complexity
            if len(template_element.find_all()) > 0:
                # Complex nested template - get full text from container
                extracted_text = matching_element.get_text(strip=True)
                extracted_text = ' '.join(extracted_text.split())  # Clean whitespace
            else:
                # Simple template - use targeted extraction
                extracted_text = extract_text_from_element(matching_element, template_element)
            
            if extracted_text:
                ##print(f"Extracted text: '{extracted_text}'")
                extracted_parts.append(extracted_text)
                processed_elements.append(matching_element)
    
    # Combine all parts and remove duplicates while preserving order
    final_parts = []
    for part in extracted_parts:
        if part not in final_parts:
            final_parts.append(part)
    
    if len(final_parts) == 3 and final_parts[0].isdigit() and final_parts[1].isdigit():
         final_result = f"{final_parts[0]}.{final_parts[1]} {final_parts[2]}"
    elif len(final_parts) == 2 and final_parts[0].isdigit() and final_parts[1].isdigit():
         final_result = f"{final_parts[0]}.{final_parts[1]}"
    else:
          final_result = ' '.join(final_parts)
    #print(f"Final result: '{final_result}'")
    return final_result
</pre>
</details>

<h2>Jokes aside: how price parser works</h2>

<p>Web scraping and data extraction system is designed to monitor product prices across multiple international retail websites. The system employs a template-based approach for HTML parsing, utilizing both Selenium WebDriver for controlling real browser for dynamic content handling and BeautifulSoup for HTML parsing. The architecture supports multi-store, multi-country price tracking with built-in inflation rate calculations and standardized unit conversions.</p>

<p>The system's flexibility stems from its configuration-driven approach. The store_config.txt file defines scraping templates for each retail store, containing structured data blocks that specify how to extract product information from different website layouts.</p>

        <h3>System workflow</h3>
        <p>The main execution flow orchestrates all system components in a coordinated sequence, processing each store configuration and extracting data for both cheapest and most expensive product variants.</p>
        
        <div class="flow-diagram">
            <div class="flow-step">Parse Configuration</div>
            <span class="arrow">→</span>
            <div class="flow-step">Initialize Database</div>
            <span class="arrow">→</span>
            <div class="flow-step">Process Each Store</div>
            <span class="arrow">→</span>
            <div class="flow-step">Extract Both Variants</div>
            <span class="arrow">→</span>
            <div class="flow-step">Save Results</div>
        </div>
        
        <h3>Processing Loop Structure</h3>
        <p>The system iterates through each store configuration, processing both cheapest and most expensive variants when URLs are available. For each variant, the system:</p>
        
        <ol>
            <li>Fetches the webpage content using Selenium WebDriver</li>
            <li>Applies template matching to extract product title and price information</li>
            <li>Processes the extracted data through the standardization pipeline</li>
            <li>Calculates derived values such as price per unit and inflation rates</li>
            <li>Saves the processed data to the database with appropriate metadata</li>
        </ol>


<h3>Configuration format structure</h3>
        <p>Each store configuration follows a standardized format with five primary sections. Let's examine the Walmart configuration as an example:</p>
        
        <pre>
STORE = Walmart
COUNTRY = USA
PRODUCT = Bread

TITLE = [
&lt;span data-automation-id="product-title" class="normal dark-gray mb0 mt1 lh-title f6 f5-l lh-copy"&gt;FFF&lt;/span&gt;
]

PRICE = [
&lt;span class="w_iUH7"&gt;current price FFF&lt;/span&gt;
]

CURRENCY_MAP = ["$": "USD"]

URLS = [
cheapest: https://www.walmart.com/search?q=bread&sort=price_low
most_expensive: 
]
        </pre>
        
        <p>
            The "FFF" placeholder acts as a dynamic content marker, indicating where the actual product data should be extracted from the webpage. This templating approach allows the system to handle diverse HTML structures across different retailers.
        </p>
        
        <h3>Configuration components</h3>
        <p>The configuration parser processes each store block by identifying key sections and extracting the relevant information:</p>
        
        <ul>
            <li><strong>Store sdentification:</strong> STORE, COUNTRY, and PRODUCT fields establish the basic metadata for each scraping target</li>
            <li><strong>HTML templates:</strong> TITLE and PRICE sections contain HTML snippets with "FFF" placeholders that guide the extraction process</li>
            <li><strong>Currency mapping:</strong> CURRENCY_MAP translates currency symbols to standardized currency codes</li>
            <li><strong>URL variants:</strong> URLS section provides endpoints for both cheapest and most expensive product sorting</li>
        </ul>
        
        <h2>Database schema and relationships</h2>
        <p>To efficiently store price tracking data across multiple dimensions the system implements a normalized relational database structure using SQLite.</p>
        
        <div class="database-table">
            <div class="table-header">Store Table</div>
            <div class="table-content">
store_id INTEGER PRIMARY KEY AUTOINCREMENT<br>
name TEXT NOT NULL UNIQUE<br>
country TEXT
            </div>
        </div>
        
        <div class="database-table">
            <div class="table-header">ProductType Table</div>
            <div class="table-content">
product_type_id INTEGER PRIMARY KEY AUTOINCREMENT<br>
name TEXT NOT NULL UNIQUE
            </div>
        </div>
        
        <div class="database-table">
            <div class="table-header">PriceSample Table</div>
            <div class="table-content">
sample_id INTEGER PRIMARY KEY AUTOINCREMENT<br>
store_id INTEGER NOT NULL<br>
product_type_id INTEGER NOT NULL<br>
date TEXT NOT NULL<br>
variant TEXT CHECK(variant IN ('cheapest', 'most_expensive'))<br>
full_name TEXT<br>
full_price_string TEXT<br>
price_number REAL NOT NULL<br>
price_currency TEXT<br>
package_size_string TEXT<br>
package_size_number REAL<br>
package_unit TEXT<br>
price_per_unit_string TEXT<br>
price_per_unit_number REAL<br>
inflation_rate REAL<br>
FOREIGN KEY (store_id) REFERENCES Store(store_id)<br>
FOREIGN KEY (product_type_id) REFERENCES ProductType(product_type_id)<br>
UNIQUE(store_id, product_type_id, date, variant)
            </div>
        </div>
        
        <p>The PriceSample table serves as the central repository, linking stores and product types while maintaining historical price data with calculated inflation rates.</p>
        
        <h2>Web scraping implementation</h2>
        <p>The system employs a dual-approach web scraping strategy, utilizing both Selenium WebDriver for JavaScript-heavy sites and falling back to HTML-based scraping for simplicity.</p>
        
        <h3>Selenium configuration</h3>
        <p>The Selenium implementation uses Firefox WebDriver with extensive customization to handle modern web security measures and anti-bot detection systems:</p>
        
<pre>
def fetch_page_selenium(url):
    firefox_options = FirefoxOptions()
    firefox_options.binary_location = r"d:\...firefox.exe"
    firefox_options.set_capability("moz:webdriverClick", False)
    firefox_options.set_preference("dom.webdriver.enabled", False)
    firefox_options.set_preference("webdriver_accept_untrusted_certs", True)
</pre>

        <h3>Template-based data extraction</h3>
        <p>The core extraction mechanism operates through a template matching algorithm that compares HTML elements from the configuration templates with actual webpage content.</p>
        
        <div class="function-box">
            <h4>find_matching_element(page_soup, template_element)</h4>
            <p>Locates HTML elements in the scraped page that match the template specifications by comparing tag names, attributes, and content patterns.</p>
        </div>
        
        <div class="function-box">
            <h4>extract_data_from_template(template_lines, page_html)</h4>
            <p>Processes template definitions to extract relevant data from webpage content, handling both simple and complex nested HTML structures.</p>
        </div>
        
        <p>The template matching process involves several steps:</p>
        
        <ol>
            <li><strong>Element identification:</strong> The system parses template HTML to identify elements containing "FFF" placeholders</li>
            <li><strong>Attribute matching:</strong> For each template element, the system searches for corresponding elements in the scraped page with matching tag names and attributes</li>
            <li><strong>Content extraction:</strong> Once matched, the system extracts the actual content replacing the "FFF" placeholder</li>
            <li><strong>Duplicate handling:</strong> The algorithm prevents duplicate extraction from nested elements through relationship tracking</li>
        </ol>
        
        <h2>Data processing pipeline</h2>
        <p>The extracted raw data undergoes comprehensive processing to standardize formats, calculate derived values, and ensure data quality before database insertion.</p>
        
        <h3>Price information processing</h3>
        <p>The <code>extract_price_info</code> function handles the complex task of extracting numerical price values from diverse string formats across different locales and currencies:</p>
        
        <pre>
def extract_price_info(price_string, currency_map):
    # Handle European decimal format (comma as decimal separator)
    if ',' in price_clean and '.' not in price_clean:
        price_clean = price_clean.replace(',', '.')
    elif ',' in price_clean and '.' in price_clean:
        # Handle format like "1.234,56" (European thousands separator)
        if price_clean.rfind(',') > price_clean.rfind('.'):
            price_clean = price_clean.replace('.', '').replace(',', '.')
        </pre>
        
            <p>The system processes different decimal and thousands separators used across various countries, ensuring accurate price extraction regardless of regional formatting conventions.</p>
        
        <h3>Package size and unit processing</h3>
        <p>Product package information extraction employs regular expressions to identify and parse size and unit data from product titles:</p>
        
        <pre>
def extract_package_info(title_string):
    patterns = [
        r'(\d+(?:[,\.]\d+)?)\s*(oz|lb|g|kg|ml|l|fl oz|г|мл|л|кг)\b',
        r'(\d+(?:[,\.]\d+)?)\s*(ounce|pound|gram|kilogram|liter|litre)\b'
    ]
        </pre>
        
        <p>The system maintains unit conversion tables to standardize measurements across different regional systems:</p>
        
        <pre>
UNIT_PATTERNS = {
    "oz": 0.0283495,
    "fl oz": 0.0295735,
    "lb": 0.453592,
    "kg": 1.0,
    "g": 0.001,
    "l": 1.0,
    "ml": 0.001,
    "г": 0.001,    # Cyrillic gram
    "мл": 0.001,   # Cyrillic milliliter
    "л": 1.0       # Cyrillic liter
}
        </pre>
        
        <h3>Price per unit calculations</h3>
        <p>The system calculates standardized price-per-unit values to enable meaningful price comparisons across different package sizes and measurement systems:</p>
        
        <pre>
            <h4>calculate_price_per_unit(price_number, package_size, package_unit, currency)</h4>
            <p>Converts package sizes to standard units (kg for weight, liter for volume) and calculates normalized price-per-unit values for comparison purposes.</p>
        </pre>
        
        <h2>Inflation rate calculation</h2>
        <p>The system incorporates temporal price change tracking by calculating inflation rates based on historical price data stored in the database. This feature enables tracking of price changes over time for each product-store combination.</p>
        
        <pre>
def calculate_inflation_rate(current_price, previous_price):
    if previous_price is None or previous_price == 0:
        return 0.0
    inflation_rate = ((current_price - previous_price) / previous_price) * 100
    return inflation_rate
        </pre>
        
        <p>The inflation calculation retrieves the most recent price record for each product-store-variant combination and computes the percentage change from the previous measurement. This enables tracking of price trends and identifying price fluctuations.</p>
        
        <h2>Error handling and data vValidation</h2>
        <p>The system implements comprehensive error handling and data validation to ensure data integrity and system reliability:</p>
        
<p>The system validates that both product title and price information are present before attempting database insertion, preventing incomplete records from corrupting the dataset.
        </p>
        
        <h3>Validation mechanisms</h3>
        <ul>
            <li><strong>Empty data checking:</strong> Validates that extracted product titles and prices contain meaningful content</li>
            <li><strong>Database constraint enforcement:</strong> Utilizes SQLite constraints to maintain referential integrity and prevent duplicate entries</li>
            <li><strong>Exception handling:</strong> Try-catch blocks protect against network failures, parsing errors, and database connection issues</li>
            <li><strong>Selenium timeout management:</strong> Implements waiting strategies to handle dynamic content loading</li>
        </ul>
        
        
        <h2>Database operations and data management</h2>
        <p>The system implements a data management strategy using SQLite with proper transaction handling and data integrity constraints.</p>
        
        <h3>Database helper functions</h3>
        <div class="function-box">
            <h4>get_or_create_store(store_name, country_name)</h4>
            <p>Implements an upsert pattern to ensure stores are uniquely identified while maintaining referential integrity in the database schema.</p>
        </div>
        
        <div class="function-box">
            <h4>get_or_create_product_type(product_name)</h4>
            <p>Manages product type records using the same upsert pattern, ensuring consistent product categorization across all stores.</p>
        </div>
        
        <p>The database operations use INSERT OR REPLACE statements to handle potential duplicate entries gracefully, ensuring that the latest price information overwrites previous entries for the same date and product combination.</p>
        
        <h2>Performance considerations and optimizations</h2>
        <p>The system incorporates several performance optimizations to handle price monitoring efficiently:</p>
        
        <ul>
            <li><strong>Connection pooling:</strong> Database connections are managed efficiently with proper opening and closing patterns</li>
            <li><strong>Batch processing:</strong> Configuration parsing and database operations are optimized for batch execution</li>
            <li><strong>Memory management:</strong> BeautifulSoup objects are created and destroyed appropriately to prevent memory leaks</li>
            <li><strong>Selenium lifecycle:</strong> WebDriver instances are properly initialized and terminated for each scraping session</li>
        </ul>
        
        <h2>Extensibility</h2>
        <p>The system architecture facilitates easy extension and maintenance through several design patterns:</p>
        
        <h3>Configuration-driven design</h3>
        <p>Adding new stores requires only configuration file updates without code modifications. The template-based approach allows the system to adapt to different HTML structures through configuration changes.</p>
        
        <h3>Modular function design</h3>
        <p>Each major operation is encapsulated in dedicated functions with clear responsibilities, making the system easier to debug, test, and extend. The separation of concerns between web scraping, data processing, and database operations enables independent modification of each component.</p>
        
        <h2>Scaper limitations</h2>
        <p>While the system provides robust price monitoring capabilities, several limitations should be considered:</p>
<ul>
            <li>Modern websites employ sophisticated anti-bot detection systems that may require ongoing adaptation of the Selenium configuration and request patterns. </li>
     <li>Website layout changes require corresponding template updates in the configuration file</li>
            <li>Network failures and temporary website unavailability require designing of respective mechanisms</li>
        </ul>
        
        <h2>Conclusion</h2>
        <p>The Product Price Parser represents an approach to automated price monitoring, combining flexible configuration management with robust data processing capabilities. The system's architecture balances complexity with maintainability, providing a scalable foundation for international price tracking. Through its template-based extraction engine, comprehensive data processing pipeline, and normalized database structure, the system enables efficient monitoring of product prices across diverse retail environments.</p>
        
        <p>The implementation demonstrates advanced web scraping techniques, proper database design principles, and thoughtful error handling strategies. The system's modular design and configuration-driven approach ensure that it can adapt to changing requirements and expanding monitoring scope without requiring significant architectural modifications.</p>
