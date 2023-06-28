# Website

## Directory
```
.
├── Pipfile
├── Pipfile.lock
├── __pycache__
│   ├── app.cpython-311.pyc
│   └── pages.cpython-311.pyc
├── app.py
├── pages.py
├── static
│   ├── bank-icon.jpeg
│   ├── city-image.png
│   ├── citybuilding.jpg
│   ├── financialservices.jpeg
│   ├── graph.png
│   ├── handshake.png
│   ├── homeimage.png
│   ├── logo.png
│   ├── money-icon.png
│   ├── solar.jpeg
│   └── styles
│       ├── banking.css
│       ├── base.css
│       ├── capitalmarkets.css
│       └── home.css
└── templates
    ├── banking.html
    ├── base.html
    ├── capitalmarkets.html
    ├── contact.html
    ├── home.html
    ├── index.html
    └── team.html
```
-------
### Banner used in all pages
###base.html
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{% block title %}Default Title{% endblock %}</title>
  {% block head %}{% endblock %}
  <link rel="stylesheet" href="{{ url_for('static', filename='styles/base.css') }}">
  {% block css %}{% endblock %}
</head>
<body>
  <div class="navbar">
    <img class="navbar-logo" src="{{ url_for('static', filename='logo.png') }}" alt="Logo">
    <ul class="navbar-menu">
      <li><a class="navbar-menu-item" href="/home">Home</a></li>
      <li><a class="navbar-menu-item" href="/banking">Banking</a></li>
      <li><a class="navbar-menu-item" href="/capitalmarkets">Capital Markets</a></li>
      <li><a class="navbar-menu-item" href="/team">Team</a></li>
      <li><a class="navbar-menu-item" href="/contact">Contact</a></li>
    </ul>
  </div>

  {% block content %}
  {% endblock %}

  <div class="footer">
    <div class="footer-row">
      <div class="footer-column">
        <h3>Quick Links</h3>
        <ul>
          <li><a href="/home">Home</a></li>
          <li><a href="/banking">Banking</a></li>
          <li><a href="/capitalmarkets">Capital Markets</a></li>
          <li><a href="/team">Team</a></li>
          <li><a href="/contact">Contact</a></li>
        </ul>
      </div>
      <div class="footer-column">
        <h3>Contact Us</h3>
        <p>Ardour Capital Investments, LLC</p>
        <p>26 Broadway Ste 1107 New York, NY 10004</p>
        <p>Phone: (347) 201-6165</p>
        <p>Email: info@ardourcapital.com</p>
      </div>
    </div>
    <div class="footer-bottom">
      <p>© 2023 Ardour Capital Investments, LLC</p>
    </div>
  </div>
</body>
</html>
```
------------------------
###base.css:
```
/* Add this at the beginning of base.css */
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

html, body {
  background-color: #f0f4f8;
  margin: 0;
  padding: 0;
  overflow-x: hidden;
}

.navbar {
  display: flex;
  font-family: Arial, sans-serif;
  justify-content: space-between;
  align-items: center;
  background-color: #1c3144;
  padding: 20px;
  position: relative;
  z-index: 1; /* Add this to bring the navbar to the front */
}

.navbar:after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 10px; /* Increase the border height */
  background: linear-gradient(to right, #003366, #1c3144, #003366);
  z-index: -1; /* Add this to position the border below the navbar */
}

.navbar-logo {
  width: 200px;
  height: auto;
}

.navbar-menu {
  display: flex;
  justify-content: space-around;
  align-items: center;
  list-style: none;
  margin: 0;
  padding: 0;
}

.navbar-menu-item {
  margin: 0 20px;
  font-size: 1.2em;
  font-weight: bold;
  text-transform: uppercase;
  color: #e0f0ff;
  text-decoration: none;
  transition: all 0.2s ease-in-out;
}

.navbar-menu-item:hover {
  color: #b4c4db;
}

.footer {
  margin-top: 20px;
  text-align: center;
  padding: 10px;
  background-color: #003366;
  color: #fff;
  font-family: Georgia, serif;
  position: relative;
  z-index: 1; /* Add this to bring the footer to the front */
}

.footer:before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 10px; /* Increase the border height */
  background: linear-gradient(to right, #1c3144, #003366, #1c3144);
  z-index: -1; /* Add this to position the border below the footer */
}

.footer-row {
  display: flex;
  justify-content: space-around;
  align-items: flex-start;
  flex-wrap: wrap;
}

.footer-column {
  flex: 1;
  padding: 20px;
}

.footer h3 {
  font-size: 1.2em;
  margin-bottom: 10px;
}

.footer ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.footer li {
  margin-bottom: 5px;
}

.footer a {
  color: #fff;
  text-decoration: none;
}

.footer a:hover {
  text-decoration: underline;
}

.footer-bottom {
  margin-top: 20px;
}
```
--------------------

##Home page (landing page)
###home.html
```
{% extends "base.html" %}

{% block title %}Home{% endblock %}

{% block css %}
  <link rel="stylesheet" href="{{ url_for('static', filename='styles/home.css') }}">
{% endblock %}

{% block content %}
  <div class="banner">
    <img class="homeimage" src="{{ url_for('static', filename='homeimage.png') }}" alt="Home Image">
    <h1 class="banner-title">Services for Institutional Investors</h1>
  </div>

  <div class="content">
    <img class="handshake" src="{{ url_for('static', filename='handshake.png') }}" alt="Businessmen Shaking Hands">
    <div class="text">
      <h2 class="green-title">ARDOUR GLOBAL INDEXES</h2>
      <p>The <strong>Ardour Global Indexes</strong> strive to include pure play alternative energy companies over a specific size. These indexes are based on extensive data and rules-based methodologies.</p>
    </div>
  </div>
{% endblock %}
```
###home.css:
```
body {
  background-color: #f0f4f8;
}

.banner {
  position: relative;
  text-align: center;
  background-color: #fff;
  border-radius: 5px;
  margin: 0 auto; 
  padding: 0; 
  overflow: hidden;
  width: 80%; 
}

.homeimage {
  width: 100%;
  height: auto;
  display: block;
  object-fit: cover;
}



.banner-title {
  position: absolute;
  color: #2f2f2f;
  font-family: Georgia, serif;
  font-size: 1.0em;
  font-weight: bold;
  text-shadow: 6px 6px 6px black;
}

.content {
  width: 80%;
  margin: 40px auto;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.handshake {
  width: 100%;
  height: auto;
  display: block;
  margin: 0 auto 20px;
}

.green-title {
  color: limegreen;
  font-family: Georgia, serif;
  font-size: 1.2em;
  font-weight: bold;
  text-align: center;
}

.text {
  font-family: Georgia, serif;
  color: #2f2f2f;
  text-align: justify;
}
```
---------------------
##Capital markets page
###capitalmarkets.html:
```
{% extends "base.html" %}

{% block title %}Capital Markets{% endblock %}

{% block head %}
  <link rel="stylesheet" href="{{ url_for('static', filename='styles/capitalmarkets.css') }}">
{% endblock %}

{% block content %}
  <div class="banner">
    <img class="city-image" src="{{ url_for('static', filename='city-image.png') }}" alt="city-image">
    <div class="banner-text-container">
      <h1 class="banner-title">Services for Institutional Investors</h1>
      <p class="banner-textbox">Our team is built up of some of the most well connected people in the clean energy industry. </p>
    </div>
  </div>

  <div class="content">
    <div class="text">
      <h2 class="green-title">ARDOUR GLOBAL INDEXES</h2>
      <p class="index-text">The Ardour Global Indexes strive to include pure play alternative energy companies over a specific size. These indexes are based on extensive data and rules-based methodologies.</p>
      <p class="index-text">We offer a wide range of products and services to meet the investment needs of institutional clients.</p>
    </div>
    <img class="handshake" src="{{ url_for('static', filename='handshake.png') }}" alt="Businessmen Shaking Hands">
  </div>

{% endblock %}
```
###capitalmarkets.css
```
/* Banner */
.banner {
  position: relative;
  text-align: center;
  padding: 0;
  margin: 0;
}

.city-image {
  width: 100.9vw;
  height: auto;
  display: block;
  object-fit: cover;
  margin-top: -20px;
  transform: translate(-2%,-0.5%); /* Add this line */
}

.banner-text {
  position: relative;
  text-align: center;
  margin-top: 1rem;
}

.banner-title {
  color: white;
  font-size: 3rem;
  font-weight: bold;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.9);
  margin-top: -24px; /* Add this line */
  padding: 0rem;
  background-color: rgba(0, 0, 128, 0.5);
  width: 100%;
  position: relative;
  top: 100%;
  left: 0;
}

.banner-textbox {
  color: darkblue;
  font-size: 1.5rem;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.4);
  margin: 0;
  padding: 0rem;
  background-color: rgba(0, 0, 0, 0);
  width: 100%;
  top: 100%;
  max-width: 800px;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
}

/* Content */
.content {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 2rem;
  margin: 2rem;
}

.handshake {
  width: 40%;
  margin-right: 2rem;
}

.text {
  width: 50%;
}

.green-title {
  font-size: 2rem;
  font-weight: bold;
  margin-bottom: 1rem;
}

.index-text {
  font-size: 1.5rem;
  line-height: 1.5;
}

```
--------------------------
##Banking page
###banking.html:
```
{% extends "base.html" %}

{% block title %}Banking{% endblock %}

{% block head %}
  <link rel="stylesheet" href="{{ url_for('static', filename='styles/banking.css') }}">
{% endblock %}

{% block content %}
  <div class="gold-banner">
    <a href="https://vettafi.com/issuer-services/indexing/finder/" target="_blank">DISCOVER THE ARDOUR GLOBAL INDEXES</a>
  </div>
  <img class="solar-image" src="{{ url_for('static', filename='solar.jpeg') }}" alt="Solar panel">
  <div class="main-content">
    <h1>Financial Services for Emerging Growth Companies</h1>
    <p class="description">Ardour Capital provides a wide range of corporate finance services to companies in their growth phase and beyond. We introduce these companies to the capital markets and to institutional investors.</p>
    <p class="contact-us">Contact us to find out more.</p>
  </div>
  <hr class="light-blue-separator">
  <div class="content-container">
    <div class="services">
      <h2>CORPORATE FINANCE &amp; INVESTMENT BANKING SERVICES:</h2>
      <div class="financialserviceslist">
        <h2>OUR SERVICES</h2>
        <ul>
          <lip>
            <div class="row">
              <div class="bullet">&bull;</div>
              <div class="col-6">Valuation Analyses</div>
              <div class="bullet">&bull;</div>
              <div class="col-6">Equity &amp; Debt Financings</div>
            </div>
          </lip>
          <lip>
            <div class="row">
              <div class="bullet">&bull;</div>
              <div class="col-6">Mergers &amp; Acquisitions</div>
              <div class="bullet">&bull;</div>
              <div class="col-6">Institutional Road Shows</div>
            </div>
          </lip>
          <lip>
            <div class="row">
              <div class="bullet">&bull;</div>
              <div class="col-6">Warrant Conversions</div>
              <div class="bullet">&bull;</div>
              <div class="col-6">Proxy Solicitations</div>
            </div>
          </lip>
          <lip>
            <div class="row">
              <div class="bullet">&bull;</div>
              <div class="col-6">Business Plan Preparation &amp; Review</div>
              <div class="bullet">&bull;</div>
              <div class="col-6">Strategic Planning</div>
            </div>
          </lip>
          <lip>
            <div class="row">
              <div class="bullet">&bull;</div>
              <div class="col-6">Project Finance</div>
              <div class="bullet">&bull;</div>
              <div class="col-6">Corporate Presentations</div>
            </div>
          </lip>
          <lip>
            <div class="row">
              <div class="bullet">&bull;</div>
              <div class="col-6">Exchange Listings (NYSE, AMEX, NASDAQ)</div>
              <div class="bullet">&bull;</div>
              <div class="col-6">Aquisitions</div>
            </div>
          </lip>
        </ul>
      </div>
    </div>
    <div class="financialservicesimage">
      <img src="{{ url_for('static', filename='financialservices.jpeg') }}" alt="Image of financial services">
    </div>
  </div>
{% endblock %}
```
###banking.css:
```
body {
  background-color: #f0f4f8;
}

.gold-banner {
  background-color: #d4af37;
  text-align: center;
  padding: 5px 0;
}

.gold-banner a {
  font-family: Georgia, serif;
  font-size: 20px;
  font-style: italic;
  color: #000;
  text-decoration: none;
}

.solar-image {
  width: 100%;
  display: block;
}

.main-content {
  text-align: center;
  margin-top: 20px;
}

h1 {
  font-size: 30px;
  font-weight: bold;
  color: #003366;
  margin: 0;
  padding: 0;
}

.description {
  font-size: 16px;
  color: #333;
  margin: 20px 0;
}

.contact-us {
  font-weight: bold;
  margin-bottom: 20px;
}

.light-blue-separator {
  border: 1px solid #B0E0E6;
  margin-bottom: 20px;
}

.content-container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  margin: 0 auto;
  max-width: 1200px;
  padding: 20px;
}

.services {
  flex-basis: 65%;
}

h2 {
  font-size: 24px;
  font-weight: bold;
  color: #333;
  margin-top: 0;
  margin-bottom: 20px;
}

ul {
  list-style: disc;
  margin: 0;
  padding: 0;
}

lip {
  margin-bottom: 10px;
  font-size: 20px;
  line-height: 1.5;
}

.financialservicesimage {
  flex-basis: 35%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.financialservicesimage img {
  max-width: 100%;
  max-height: 100%;
}

.row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
}

.col-6 {
  width: 45%;
  font-size: 20px;
  line-height: 1.5;
}

.row lip {
  display: inline-block;
  margin-right: 10px;
}
```
-------------------------
##Team page
###team.html:
```
{% extends "base.html" %}

{% block title %}Team{% endblock %}

{% block content %}
    <h1>Ardour Team and Advisors</h1>

    <h2>Officers and Key Employees</h2>

    <h3>Kerry Dukes, Co-founder, and Managing Partner</h3>
    <p>Mr. Dukes is responsible for Corporate Finance, Company organization, financing and compliance aspects of the business. Mr. Dukes has over 28 years of experience in the investment banking and securities industry. Prior to Ardour, Mr. Dukes served as Founder/Senior Managing Partner/Head of Global Activities of BlueStone Capital Partners from 1995 to 2001 where Mr. Dukes grew the firm’s brokerage operations from 0 to $62 million dollars in revenues and was instrumental negotiating and selling a significant interest in the company to ABN Amro Bank, N.V. for $62.5 million dollars. Prior to Bluestone, Mr. Dukes served as Chief Operating Officer and Managing Director of Commonwealth Associates from 1988 to 1995. Through his career, Mr. Dukes has managed over 100 public and private offerings. He has served on the board of numerous public companies and has testified as an industry expert witness. He has also acted as a moderator, and guest speaker at the NASD sponsored “New Issue and Regulatory Development Conference” in Washington. Mr. Dukes began his career in the management-training program at Shearson Lehman in 1982.</p>

    <h3>Brian Greenstein, Co-founder and Managing Partner</h3>
    <p>Brian has over 28 years’ experience in the financial services industry and is responsible for the development and execution of the company's capital markets activities. Prior to co-founding Ardour, Mr. Greenstein was Managing Director of Capital Markets at Bluestone Capital Partners from 1996 to 2001, where he was responsible for institutional sales and syndicate Prior to Bluestone, Mr. Greenstein was Managing Director of Institutional Sales at Commonwealth Associates from 1991 to 1996. His previous brokerage affiliations include Bear Stearns and Merrill Lynch. He was responsible for marketing the asset management services of ITT/Hartford to the qualified plan market. He began his career in the actuarial field as an associate with George Buck Consulting Actuaries in 1981.</p>

    <h3>Walter Nasdeo, Managing Director</h3>
    <p>Walter is a Managing Director in the Investment Banking group. Prior to that he supervised Ardour’s Energy Technology group and was responsible for the equity research effort. Previously Vice President of research and head of energy technology team at Bluestone Capital. At Credit Lyonnais Securities he researched consolidating industries. Walter has frequently appeared on CNBC, Bloomberg, and The BBC. He has also presented at numerous energy technology conferences and been quoted in various publications including The Wall Street Journal, New York Times, CNNMoney, CNNfn, The Street.Com, Bloomberg News, Small Times, Sustainable Business.com, Dow Jones Newswire. He has been named a Bulldog Research Award Winning Analyst for earnings accuracy. Walter received his MBA and his BBA in Entrepreneurship from the University of North Texas. He served in the U.S. Army European Operations, Berlin, Germany, and held a secret security clearance as a member of the Berlin Brigade in the 1980s.</p>

    <h3>Jean-Marc O’Brien, Director</h3>
    <p>Marc has 37 years’ experience in institutional sales, sales management, and trading. He was Director of New Business Development, Medley Global Advisors 2004-2005. He held Senior Capital Markets positions with Credit Agricole Indosuez Securities in New York, Paris and, Stockholm. Previously he was Manager of Fixed Income Sales in Paris from 1989 to 2001. He started his career at Citibank NA 1983-1989. He is a graduate of the M&T Program of the University of Pennsylvania ( Wharton and Engineering) and is fluent in five languages.</p>

    <h3>Michael Garvey, Director, Investment Banking</h3>
    <p>Mike is a Director, Investment Banking and has over 25 years of financial experience. Mr. Garvey was the Managing Member of Two River Solutions, LLC a financial consulting firm providing valuation, research, and other financial services. Previously, Mr. Garvey was Chief Financial Officer at Cavaloz Oil & Gas, LLC and has held various research and portfolio management roles at Schottenfeld Group, Longbow Capital Partners, Four Points Partners, the Galleon Group, Angelo, Gordon & Co. and CIBC World Markets Corp (formerly Oppenheimer & Co). Mr. Garvey has extensive experience in financial analysis and business valuations from both the external investment/advice and internal company perspectives. Mr. Garvey’s experience includes both sell-side and buy-side research in energy, utilities, and related industries and includes energy research covering exploration and production, oil service, refining, pipelines, and midstream. Mr. Garvey holds a Bachelor of Business Administration in Accounting from Hofstra University.</p>

    <h3>Brendan Dukes, Vice President</h3>
    <p>Vice President-Prior to joining  Ardour Capital in 2019  Brendan was Vice President in Debt Capital Markets at Madison Parker Financial a specialist in leveraged lending. Brendan graduated from James Madison University with a BA in Economics and a minor in Law</p>

    <h2>Advisors:</h2>

    <h3>Jonathan Treacher</h3>
    <p>Jonathan has over 30 years of investment banking, fund management and board level senior management experience. He has been Chairman (formerly CEO) of Absolute Capital Management where he was instrumental in formulating and executing the successful restructuring and performance. He was a Director at Farlake Group PLC; an AIM quoted asset management business that grew from L250-800. He executed the sale of this business to a London investment bank. Share price rose from 180p to 780p. Jonathan was founder and director of an emerging markets fund Romanian Reconstruction Capital where there was a 4x value increase during his tenure. From 1998-2002 at Oakes Fitzwilliams & CO, he executed numerous corporate finance mandates. He was the co-founder of the Amoeba Fund an early stage biotechnology fund from 1998-2003. He founded Prokom A.O. a Novosibirsk, Russia focused fund which liquidated after 30% IRR was returned to investors. Previous affiliations were with European Capital Partners, Benchmark Group, Drexel Burnham Lambert1, Hill Samuel & Co Limited. His education includes advanced education at the London Business School, Hague Academy of International Law and DePaul University School of Law.</p>
    <p1>Tom managed a Global Investment Fund focused in Emerging Markets from 2014 to 2018. From 2005 to 2013 Tom was an Equity Portfolio manager for George Weiss Associates, a Large Multi-Strategy Hedge Fund. His Geographic focus was Latin America, Greater China, and Russia. Previous to GW, Tom was a partner and founder of Miami based INCA Fund, an equity investment fund focused on Latin America. Before founding INCA Tom ran a boutique advisory firm focused on providing PIPE financing/advisory to Brazilian companies while also consulting for Acon Investments, a Private Equity fund and, TPG subsidiary.</p1>
    <p2>From 1998 to 2001 Tom was head of Equities and Risk for CLSA Emerging Markets New York Office. Prior to CLSA Tom held various senior positions in sales and management for a number of Investment banks including Bear Stearns, Credit Agricole, ING/Barings, WI Carr, and Merrill Lynch. Tom has been a founder and Board Member of a number of companies including The Spanish Beisbol Network, Banco Galicia de Venezuela, and Grow VC and is an advisor to LDJ Capital, a multi-family office. He is currently on the board of directors of Atom Participacoes, an education company listed in Brazil. Tom is a graduate of Columbia University.</p2>
    
    <h3>Thomas Samuelson</h3>
    <p>Tom has had a diverse 30-year career in finance. Currently, Tom is the CEO of Magellan Yates LLC which advises and supports public companies in Latin America and Emerging Markets on Digital IR initiatives.</p>

    <h3>Nicholas Rohleder</h3>
    <p>Mr. Rohleder is the Co-Founder and Environmental Technology Portfolio Manager at New American Energy. Mr. Rohleder is responsible for the implementation of the firm’s pure play alternative energy and sustainability strategy. Prior to this, Mr. Rohleder served as the Chief Operating Officer of Merit Holdings Group, an ESG and sustainability focused private investment platform. At Merit, Mr. Rohleder was responsible for risk management and operations across all verticals. Mr. Rohleder began his career at Dwight Capital, a diversified financial services firm encompassing private debt, private equity, a fixed income fund, and an asset-based lender. Nick is regularly quoted media outlets such as Forbes, Hedge Fund Monthly, and Energy Trend for commentary on global energy and financial markets. Mr. Rohleder is actively involved with the Earth Institute at Columbia University, The Columbia Center on Global Energy Policy, and The Columbia/Penn Club of New York City, The Tulsa Chamber of Commerce, and Sustainable Tulsa. Mr. Rohleder graduated Summa Cum Laude and Phi Beta Kappa from the University of Oklahoma with degrees in Economics and Political Science. Mr. Rohleder received his Master of Science in Sustainability Management degree from Columbia University with a focus in Environmental Business and Environmental Economics.</p>

    <h3>Andrew Gold</h3>
    <p>Mr. Gold is the Co-Chief Investment Officer at New American Energy. Mr. Gold possesses extensive experience in traditional energy, industrial and petroleum engineering, and investment management. Prior to joining New American Energy, Mr. Gold was a Portfolio Manager at Alhambra Holding Inca multi-strategy asset management firm. Andrew began his career as an engineering consultant for HP Engineering. Mr. Gold received his undergraduate degree in Mechanical Engineering from Texas Christian University. Mr. Gold received his Master of Business Administration from the University of Tulsa.</p>
{% endblock %}

```
----------------------
##Contact
###contact.html:
```
{% extends "base.html" %}

{% block title %}Banking{% endblock %}

{% block content %}
    <h1>Ardour Capital</h1>
    <h1>Contact</h1>
{% endblock %}
```

