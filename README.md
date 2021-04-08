
# Rapport

**Rapport Assignment 2: Webview**

Uppgiften gick ut på att skapa en app som länkar till två hemsidor. En intern som ligger lokalt och en extern sida som ligger på en server.

För att möjligöra detta krävs det att en ny webbvy i Android och man skapar ett nytt objekt och skapar en ny vy i xml layout som är Webview.
Koden nedan är xml och har layout och ett id som sedan kommer läsas från koden och köras när den anropas.

```
<WebView
    //Detta är koden med ett unikt id.
    android:id="@+id/my_webview"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    />
 
 ```
 Här börjar koden att läsa in id:t och hämtar layouten för det objektet.
 För att sedan skapa detta objekt krävs följande kod:
 ```
 @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Toolbar toolbar = findViewById(R.id.toolbar);
        setSupportActionBar(toolbar);
        
        myWebView = (WebView) findViewById(R.id.my_webview);
        myWebView.setWebViewClient(new WebViewClient());
        //Här sätts att javascript ska köras på sidan.
        myWebView.getSettings().setJavaScriptEnabled(true);
```
Här refererar myWebView till layouten i XML som skapades tidigare. Och länkas genom findViewById. Sedan sätts det att WebView kan köra JavaScript.

```
    public void showExternalWebPage(){
        // TODO: Add your code for showing external web page here
        myWebView.loadUrl("https://wwwlab.iit.his.se/a19jimsa/Mobilapplikationsdesignprojekt/");
    }

    public void showInternalWebPage(){
        // TODO: Add your code for showing internal web page here
        myWebView.loadUrl("file:///android_asset/about.html");
    }
```
När respektive funktion körs kommer sidan laddas in som antingen är lokal eller extern och ritas ut i webbvyn. Beroende på vilken man väljer i menyn. Sidan som laddas in som intern är en html fil som är skapad och tillagd i android-mappen asset.

Så här ser resultatet ut för interna sidan:

![](intern.png | width=100)

och så här för externa hemsidan:

![](extern.png | width=100)
