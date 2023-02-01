# פיתוח אפליקציית belle לshopify
## חלק ראשון - היכרות בסיסית עם shopify ויצירת אפליקציה פשוטה

### כמה מושגים בסיסיים: 
א. shopify זו פלטפורמה ליצירת חנויות דיגיטליות, בלי צורך בקוד, סטייל וויקס רק לחנויות.
השימוש הבסיסי הוא חינמי, והחנות כוללת גם ממשק ניהול, עם אופציה לשנות ערכות נושא, לשלוט על המלאי וכו.
שם גם יש אפשרות להוריד אפליקציות שמיועדות לshopify, הן אמורות לעזור לסוחרים בכל מני נושאים.
בהקשר של belle זה המלצות וניהול מלאי.

ב. shopify partner הוא ממשק של shopify לכל הצד של המציעים תמיכה לסוחרים. במקרה שלנו זה יהיה הצד של הפיתוח (פיתוח אפליקציות מן הסתם).

ג. בשביל להבין את ההמשך, מומלץ פשוט לפתוח חשבון חינמי, לפתוח חנות, ולשחק עם הממשק שם במשך כמה זמן.

ד. איך אפליקציה בshopify עובדת - וזה קצת טריקי. מה שמוצג בממשק של shopify, זה iframe של אתר, שבו הקוד שלנו רץ. אתר, כפשוטו, עם כתובת והכל. אם ננסה להכנס לכתובת הזו מהדפדפן, לא נצליח כי צריך הרשאה שיש רק לחנות בshopify, אבל העקרון הוא זהה לחלוטין לכל אתר רגיל שאנחנו מכירים ברשת.

ה. איך פיתוח אפליקציה בshopify עובד - בשביל לפתח אפליקציה, shopify יצרו מעין create-react-app שיוצר תבנית של קוד של אפליקציה, שעליה אפשר לכתוב את הקוד שלנו (יש בכמה שפות, אנחנו נשתמש בnodejs). איך הפיתוח עצמו עובד? זה גם קצת טריקי. בשביל שנוכל לראות בזמן אמת איך האפליקציה נראית בממשק ניהול של חנות, אנחנו נעלה את הlocalhost שבו אנחנו מפתחים בדרך כלל, לשרת שיושב ברשת, בעצם הקוד שלנו ירוץ בו, ממש כמו localhost, וכל שינוי שלנו יתעדכן גם שם. השרת הזה, יוצג בiframe בממשק של shopify. ממילא גם במהלך הפיתוח, נצטרך להתקין את האפליקציה שלנו בחנות, בשביל לראות איך הדברים רצים שם בזמן אמת.

ו. בשביל השרת הזה, נשתמש בפלטפורמה בשם ngrok.

הדברים פחות מסובכים מאיך שהם נשמעים, כי רוב הדברים שכתובים פה באים ועובדים אוטומטית עם התבנית של shopify.

**הערה חשובה - לאחרונה התבנית של shopify השתנתה מnextjs לreact vite + exepress. האפליקצייה belle כתובה על התבנית של nextjs.
**עוד הערה- כל הלינקים כאן וגם המהלך יכול קצת להשתנות עם הזמן. אבל העקרון יהיה בערך אותו הדבר, בכל מקרה מומלץ להעזר בדוקומנטציה של shopify.



### אפליקציית shopify פשוטה:

אז המטרה שלנו היא לפתח אפליקציה לshopify, האפליקציה belle כבר קיימת, אבל בשביל התרגול, נבנה אפליקציה פשוטה בהתאם לדוקומנטציה של shopify. 
נצטרך חשבון בshopify partner, וחנות לדוגמה.

פתיחת חשבון shopify partner-
https://partners.shopify.com/signup

פתיחת חנות לפיתוח לדוגמה-
https://shopify.dev/apps/tools/development-stores#create-a-development-store-to-test-your-app

נכנס לטרמינל ונכתוב:
```sh
$ npm init @shopify/app@latest
```

מכאן העקרון יהיה דומה לcreate-react-app.
נבחר שם לאפליקציה, פלטפורמה (node) והתבנית והתלויות יותקנו לבד.

נכנס לתיקייה שנוצרה (בשם שבחרנו) ונכתוב:
```sh
$ npm run dev
```
מכאן shopify cli יבקש להתחבר לחשבון shopify partner, ולוודא שיש חנות לפיתוח (שיצרנו כבר).
וליצור חשבון בngrok, לפתוח את הקישור ולהדביק את הטוקן שהוא ייצר.

תופיע שורה בטרמינל בשם Shareable app URL וקישור. נכנס לקישור ונגיע לחנות שלנו, עם אופציה להתקין את האפליקציה בה.
ומיד היא תופיע לנו תחת השורה apps בצד שמאל, כמו כל אפליקציה.

אם נשנה משהו בקוד, הוא יתעדכן שם אוטומטית כל עוד השרת בטרמינל רץ.
אם הכל עבד עד לכאן אז הצלחנו!

בחלק השני נכתוב על הקוד עצמו ובפרט על הספריות הבסיסיות של כל shopify app:

@shopify/polaris,

@shopify/app-bridge
