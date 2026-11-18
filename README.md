# Routecraft — ট্রাফিক প্ল্যান ম্যাপ এডিটর

একটি ফ্রি, স্ট্যাটিক ওয়েব অ্যাপ—ব্যক্তিগত অফিসের ট্রাফিক ম্যানেজমেন্ট প্ল্যান, রুট, প্রবেশপথ, সীমাবদ্ধ এলাকা এবং নিরাপত্তা নোট সাজানোর জন্য। এটি Mapz-এর সাধারণ map-edit/export workflow থেকে অনুপ্রাণিত একটি স্বতন্ত্র প্রকল্প; Mapz-এর কোড, মানচিত্র বা ডিজাইন অ্যাসেট কপি করা হয়নি।

## লোকালি চালানো
`index.html` আধুনিক ব্রাউজারে খুলুন, অথবা এই ফোল্ডারকে যেকোনো static web server দিয়ে serve করুন। ম্যাপ টাইল, স্থান অনুসন্ধান, KMZ পড়া এবং PNG capture-এর জন্য ইন্টারনেট লাগবে।

## GitHub Pages-এ প্রকাশ
1. GitHub-এ একটি repository তৈরি করে এই ZIP-এর ভেতরের সব ফাইল repository root-এ upload করুন (`index.html` যেন root-এ থাকে)।
2. **Settings → Pages → Deploy from a branch** নির্বাচন করুন; branch `main` এবং folder `/(root)` দিয়ে Save করুন।
3. GitHub Pages deployment শেষ হলে দেখানো URL খুলুন।

কোনো build command বা API key লাগবে না।

## ব্যবহার
- মানচিত্রে Route, Restricted area, Marker, Text label এবং Hazard আঁকুন; আইটেম বেছে নাম, নোট, রঙ, opacity, line style ও width বদলান।
- বাম পাশের **Import** দিয়ে `.kmz`, `.kml`, `.csv`, `.geojson` বা `.json` ফাইল যোগ করুন।
- CSV-তে header হিসেবে `lat,lon` অথবা `latitude,longitude` থাকতে হবে। `name`, `description`, `type` ও `route`/`group` কলাম ঐচ্ছিক। একই route/group নামের সারিগুলো route হিসেবে জোড়া হবে।
- **Export → Page layout studio** খুলে A4/A3/A2/A1/Letter/Legal অথবা custom size, Portrait/Landscape, তিন স্তরের শিরোনাম এবং প্রতিটি sheet-এ map, legend, north arrow, scale bar, latitude/longitude frame ও footer on/off করুন। Map frame-টি sheet-এর মধ্যে টেনে সরানো যায়; slider দিয়ে মাপ বদলান। **Add sheet** দিয়ে একাধিক পৃষ্ঠা বানিয়ে **Export all pages** দিয়ে একসঙ্গে Print / Save as PDF করুন।
- **Save plan** JSON-এ map features ও print-layout settings একসঙ্গে ডাউনলোড করে; **Open** দিয়ে আবার তুলুন। Draft-ও এই ব্রাউজারে auto-save হয়।

## ডেটা, সেবা ও সীমাবদ্ধতা
- Map tiles © [OpenStreetMap contributors](https://www.openstreetmap.org/copyright); public tile server-এর [ব্যবহারের নিয়ম](https://operations.osmfoundation.org/policies/tiles/) ও attribution মেনে চলুন। Light/Dark basemap-এর জন্য CARTO public tiles ব্যবহার করা হয়। Search-এর জন্য Nominatim ব্যবহৃত হয়; তাদের [usage policy](https://operations.osmfoundation.org/policies/nominatim/) মানুন।
- KMZ import-এর জন্য JSZip CDN, এবং PNG/PDF layout capture-এর জন্য html2canvas CDN ব্যবহৃত হয়; এসব লাইব্রেরি load হতে ইন্টারনেট প্রয়োজন।
- Export করা SVG-তে editable plan annotations থাকে; basemap tiles embed করা হয় না।
- PNG/PDF basemap capture ব্রাউজার বা tile-service CORS নিয়মে বাধা পেতে পারে। সেক্ষেত্রে **Refresh map preview** চেষ্টা করুন; তারপরও না হলে map data export/Print fallback ব্যবহার করুন। Print-PDF-এর map snapshot হলো বর্তমান screen view-এর high-resolution raster capture—মূল basemap-এর zoom/detail উৎস টাইলের ওপর নির্ভরশীল।
- CSV-তে location point এবং route/group coordinate-গুলো সমর্থিত। KMZ/KML-এ Point, LineString, Polygon আমদানি হয়।
- এটি পরিকল্পনার সহায়ক টুল, অনুমোদিত নিরাপত্তা বা জরুরি প্রবেশ-পরিকল্পনার বিকল্প নয়। বাস্তব সাইটের অবস্থা ও প্রযোজ্য নিরাপত্তা-নিয়ম যাচাই করুন।
