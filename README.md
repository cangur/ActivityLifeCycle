# Activity Lifecycle

Activity Lifecycle, Anroid uygulamalarının birincil bileşenidir. Bu makalede Activity Lifecycle hakkında bilgiler verip, yaşam döngüsü ve uygulanması ele alınacaktır.

## Activity

Activity, kullanıcının arayüzünde gözüken bir ekrandır. Tıpkı Java uygulamalarındaki bir pencere veya herhangi bir web sitesindeki bir web sayfası gibi. Android uygulamaları, temel olarak birbiriyle etkileşime giren birden çok etkinlikten oluşan bir kombinasyondur. Her uygulama, uygulama başlatıldığında oluşturulan tek bir Launcher Activity'e sahiptir. Uygulama başlatıldığında gördüğünüz ekran budur. Bu Launcher Activity kullanıcı etkileşimine yanıt olarak diğer etkinlikleri başlatabilir.

## Activity Lifecycle

Daha önce de söylediğim gibi, etkinlik, uygulamanın kullanıcı etkileşimine yanıt veren tek bir ekrandır; bu nedenle, bir uygulamayı başlattığınızı varsayalım (ActivityA). Bu activity üzerinde herhangi bir düğmeye tıklama, daha sonra size görünür olacak yeni bir etkinliği (Activity B) başlatabilir ve eski activity artık görünmez. Yani ilk activity yok etmiş oldunuz.

Temelde Activity A aşağıdaki stateleri geçirdi

<p align="center">
 <b>Created -> Visible -> Invisible -> Destroyed</b>
</p>

Her Android uygulamasında, activiylerin geçirdiği bu stateler sırasında yapılacak işlemler aşağıda gösterilen şemada isimleri geçen metodlar sayesinde yapılır.

<p align="center">
 <img src="https://androidclarified.files.wordpress.com/2017/07/activity_lifecycle.jpg">
</p>

###### onCreate()
- Bu, bir etkinliğin aldığı ilk callback metodudur. Activity ilk oluşturulduğunda çağırılır. Activiy'nin kullanıcı arayüzünü bağladığı yerdir.
```ruby
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
 
        Log.d(TAG, "The onCreate() event");
        setContentView(R.layout.activity_main);
    }
```

###### onStart()
- Bu metod, etkinliğin başlatılmış duruma girdiğini gösterir. Activity görünür hale geldiğinde çağırılır. Ayrıca Activity görünür ancak etkileşimli olmadığında çağrılır.
```ruby
    @Override
    protected void onStart() {
        super.onStart();
        Log.d(TAG, "The onStart() event");
    }
```

###### onResume()
- Bu metod, activity'nin devamlı duruma girdiğini gösterir. Temel olarak activity ön planda ve kullanıcı artık activity ile etkileşime geçebilir demektir.
```ruby
    @Override
    protected void onResume() {
        super.onResume();
        Log.d(TAG, "The onResume() event");
    }
```
###### onPause()
- Bu metod, activity'nin duraklatılmış duruma girdiğini gösterir. Temel olarak kullanıcının şimdi activity'i terk ettiğine dair bir göstergedir. Genellikle odağın activity'den uzaklaştığı durumlarda çağırılır. Yani örnek verecek olursak bir telefongörüşmesi alındığında ekranın kapanması veya homa butonuna basmak.
```ruby
    @Override
    protected void onPause() {
        super.onPause();
        Log.d(TAG, "The onPause() event");
    }
```

###### onStop()
- Bu metod, activity'nin durdurulmuş duruma girdiğini gösterir. Activity'nin artık görünür olmadığını gösterir.
```ruby
    @Override
    protected void onStop() {
        super.onStop();
        Log.d(TAG, "The onStop() event");
    }
```

###### onDestroy()
- Activity'nin aldığı son callback metodudur. Bu metod, bir activity sona erdirilmeden hemen önce çağırılır.
```ruby
    @Override
    public void onDestroy() {
        super.onDestroy();
        Log.d(TAG, "The onDestroy() event");
    }
```






