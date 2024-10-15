# پیام بدید
هم گروهی های عزیز لطفا به این آیدی تلگرامی @MAmirereza پیام بدید.

# تمرین جستجوی آگاهانه 
**مقدمه**

کد این پروژه از چندین فایل پایتون تشکیل شده است که برخی از آنها را برای تکمیل تکلیف باید این کد ها را بخوانید و درک کنید ( برخی از آنها را نادیده بگیرید).

**فایل هایی که ویرایش می کنید:**

جایی که همه الگوریتم های جستجوی شما در آن قرار دارند:	Search.py	

جایی که همه عوامل مبتنی بر جستجوی شما قرار دارند:	searchAgents.py	

**فایل هایی که ممکن است بخواهید به آنها نگاه کنید:**

فایل اصلی که بازی های PACMAN را اجرا می کند. این فایل یک نوع PACMAN GAMESTATE را توصیف می کند که شما در این پروژه از آن استفاده می کنید:	pacman.py

این فایل چندین SUPPORTING TYPE مانند AGENTSTATE، AGENT، DIRECTION و GRID را توصیف می کند:	game.py

ساختار داده های مفید برای پیاده سازی الگوریتم های جستجو:	util.py	
	
**فایل های پشتیبانی (می توانید نادیده بگیرید):**

گرافیک برای پکمن :	   graphicsDisplay.py

پشتیبانی از گرافیک پکمن:	graphicsUtil.py

گرافیک ASCII برای پکمن:	textDisplay.py

کنترل ارواح:	ghostAgents.py

کنترل پکمن با صفحه کلید:	keyboardAgents.py

	layout.py
        autograder.py
	testParser.py	
 	testClasses.py
  	test_case.py
   	searchTestClasses.py
    
**به بازی PACMAN  خوش آمدید**

 شما میتوانید با دستور زیر Pacman  را اجرا کنید: 
 ```python
 Python pacman.py
```
آسان ترین  agent  در فایل searchAgent.py  قرار دارد، به نام GoWestAgent که همیشه به سمت غرب میرود  ( که یک reflex agent است). با دستور زیر میتوانید GoWestAgent را اجرا کنید :
```python 
python pacman.py --layout testMaze --Pacman GoWestAgent
```
اما اوضاع برای این عامل وقتی که نیاز به چرخیدن باشد، بد می‌شود:
```python
python pacman.py --layout tinyMaze --Pacman GoWestAgent
```	
هنگامی که Pacman  به مشکلی برخورد میتوانید با CTRL+C  از برنامه خارج شوید.


توجه داشته باشید که pacman.py از تعدادی گزینه پشتیبانی می‌کند که هر کدام می‌توانند به صورت طولانی (مثلاً --layout) یا به صورت کوتاه (مثلاً -l ) بیان شوند. می‌توانید لیست تمام گزینه‌ها و مقادیر پیش‌فرض آنها را از طریق مشاهده کنید:	
```python
python pacman.py -h
```	







# **سوال 1:** یافتن نقطه های غذا با استفاده (DFS)
در فایل searchAgents.py، شما یک عامل جستجو (SearchAgent) کاملاً پیاده‌سازی شده خواهید یافت که مسیری را از دنیای پک‌من برنامه‌ریزی کرده و سپس آن مسیر را گام به گام اجرا می‌کند.

الگوریتم‌های جستجو برای برنامه‌ریزی مسیر پیاده‌سازی نشده‌اند. این وظیفه شماست:

+ ابتدا، برای اطمینان از اینکه  SearchAgent  به درستی کار می‌کند، با اجرای دستور زیر آن را تست کنید:
```python 
python pacman.py -l tinyMaze -p SearchAgent -a fn=tinyMazeSearch
```
دستور بالا به عامل جستجو (SearchAgent) می‌گوید که از tinyMazeSearch به عنوان الگوریتم جستجوی خود استفاده کند، که در فایل search.py پیاده‌سازی شده است. pacman باید به ‌طور موفقیت‌ آمیز در هزارتو حرکت کند.
+ اکنون زمان آن است که توابع جستجوی عمومی کامل بنویسید تا به Pacman در برنامه‌ریزی مسیرها کمک کنید! شبه ‌کد الگوریتم‌های جستجویی که خواهید نوشت، در اسلایدهای درس موجود است. به یاد داشته باشید که یک گره جستجو باید نه تنها شامل یک حالت باشد، بلکه اطلاعات لازم برای بازسازی مسیر (برنامه) که به آن حالت می‌رسد را نیز داشته باشد.
**نکته مهم:** تمامی توابع جستجوی شما باید فهرستی از اقدامات را برگردانند که عامل را از نقطه شروع به هدف هدایت کنند. این اقدامات باید همه حرکت‌های قانونی باشند (جهت‌های معتبر، بدون عبور از دیوارها)
  
**نکته مهم:** حتماً از ساختارهای داده Stack (پشته)، Queue (صف) و PriorityQueue (صف اولویت‌دار) که در فایل util.py ارائه شده‌اند، استفاده کنید! این پیاده‌سازی‌های ساختار داده دارای ویژگی‌های خاصی هستند.	

+ الگوریتم  DFS را در تابع depthFirstSearch در فایل search.py پیاده‌سازی کنید. برای کامل کردن الگوریتم خود، نسخه جستجوی گراف DFS را بنویسید که از توسعه دادن حالت‌های بازدیدشده جلوگیری می‌کند.
+ الگوریتم شما باید بتواند راه حل مناسبی برای سوالات زیر پیدا کند:
```python
python pacman.py -l tinyMaze -p SearchAgent
python pacman.py -l mediumMaze -p SearchAgent
```
 + ا pacman نمایشی از حالت‌های جستجو ‌شده و ترتیب جستجو آنها را نشان می‌دهد (قرمز روشن‌تر به معنی جستجو زودتر است). آیا ترتیب جستجو همان‌طور که انتظار داشتید، بود؟ آیا پک‌من واقعاً به تمام مربع‌های جستجو‌شده در مسیر خود به هدف می‌رسد؟  .
 **راهنما:** اگر از یک Stack به عنوان ساختار داده استفاده کنید، راه‌حلی که الگوریتم DFS شما برای mediumMaze پیدا می‌کند باید طولی برابر با 130 داشته باشد (مشروط بر اینکه جانشین‌ها را در ترتیب ارائه شده توسط getSuccessors به لبه (fringe) اضافه کنید؛ اگر آنها را در ترتیب معکوس اضافه کنید، ممکن است 246 دریافت کنید). آیا این راه ‌حل کم ترین‌هزینه را دارد؟  اگر نه، به این فکر کنید که DFS  چه چیزی را اشتباه انجام می‌دهد.
 
# **سوال 2:** Breadth First Search
الگوریتم   BFS را در تابع breadthFirstSearch در فایل search.py پیاده‌سازی کنید. دوباره، یک الگوریتم جستجوی گراف بنویسید که از گسترش هر حالت بازدیدشده جلوگیری کند. کد خود را به همان روشی که برای DFS تست کردید، آزمایش کنید.
```python
python pacman.py -l mediumMaze -p SearchAgent -a fn=bfs
python pacman.py -l bigMaze -p SearchAgent -a fn=bfs -z .5
```
راهنما: اگر pacman  به ارامی حرکت میکند frametime 0 – را امتحان کنید.	

## سوال 3: A* Search  
الگوریتم جستجوی A* را در تابع خالی `aStarSearch` در فایل `search.py` پیاده‌سازی کنید. الگوریتم A* یک تابع heuristic را به عنوان ورودی می‌گیرد. توابع Heuristic دو ورودی می‌گیرند: یک حالت در مسئله جستجو (ورودی اصلی) و خود مسئله (برای اطلاعات مرجع). تابع `nullHeuristic` در فایل `search.py` یک مثال ساده است.  
می‌توانید پیاده‌سازی A* خود را بر روی مسئله اصلی پیدا کردن مسیر در یک هزارتو به یک موقعیت ثابت با استفاده از تخمین فاصله منهتن (که قبلاً به عنوان `manhattanHeuristic` در فایل `searchAgents.py` پیاده‌سازی شده است) آزمایش کنید.

### راهنما
علاوه بر اینکه حالت‌های بازدید شده را پیگیری می‌کنید، ممکن است بخواهید بهترین هزینه مسیر را نیز دنبال کنید. برخی از گره‌ها ممکن است بیش از یک بار توسعه داده شوند تا مسیر بهینه پیدا شود.

```bash
python pacman.py -l bigMaze -z .5 -p SearchAgent -a fn=astar,heuristic=manhattanHeuristic
```

می‌بینید که A* راه‌حل بهینه را کمی سریع‌تر از جستجوی هزینه یکنواخت (حدود 549 در مقابل 620 گره جستجوی گسترش‌یافته در پیاده‌سازی ما، اما اولویت برابر ممکن است اعداد شما را کمی متفاوت کند) پیدا می‌کند. در `openMaze` چه اتفاقی برای استراتژی‌های مختلف جستجو می‌افتد؟

---

## سوال نمره مثبت: Varying the Cost Function
در حالی که BFS کوتاه‌ترین مسیر از نظر تعداد اقدامات را به هدف پیدا می‌کند، ممکن است بخواهیم مسیرهایی را که از نظر دیگری 'بهترین' هستند نیز پیدا کنیم. به عنوان مثال، `mediumDottedMaze` و `mediumScaryMaze` را در نظر بگیرید.  
با تغییر تابع هزینه، می‌توانیم Pacman را ترغیب کنیم تا مسیرهای متفاوتی پیدا کند. برای مثال، می‌توانیم هزینه بیشتری برای قدم‌های خطرناک در مناطق پر از ارواح تعیین کنیم یا هزینه کمتری برای قدم‌های در مناطق پر از غذا، و یک عامل Pacman منطقی باید رفتار خود را با توجه به این تغییرات تنظیم کند.

### پیاده‌سازی UCS
الگوریتم UCS را در تابع `uniformCostSearch` در فایل `search.py` پیاده‌سازی کنید. توصیه می‌کنم نگاهی به فایل `util.py` بیندازید تا با برخی از ساختارهای داده که ممکن است در پیاده‌سازی شما مفید باشند، آشنا شوید.  
اکنون باید رفتار موفقیت‌آمیز در هر دو چیدمان زیر را مشاهده کنید، جایی که تمام عامل‌های زیر UCS هستند که تنها در تابع هزینه‌ای که استفاده می‌کنند متفاوت هستند (عامل‌ها و توابع هزینه برای شما نوشته شده‌اند):

```bash
python pacman.py -l mediumMaze -p SearchAgent -a fn=ucs
python pacman.py -l mediumDottedMaze -p StayEastSearchAgent
```

### توجه
به دلیل توابع هزینه نمایی (برای جزئیات به فایل `searchAgents.py` مراجعه کنید)، باید هزینه مسیر بسیار کم برای `StayEastSearchAgent` و هزینه مسیر بسیار زیاد برای `StayWestSearchAgent` دریافت کنید.

