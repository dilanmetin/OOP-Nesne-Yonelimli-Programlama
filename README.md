# OOP-Nesne-Yonelimli-Programlama
<b>OOP nedir?</b>

OOP : Object Oriented Programming, Türkçede ise; Nesne Yönelimli Programlama demektir.

OOP, Sınıf(Class) ve Nesne(Object) kavramına dayanan bir programlama yaklaşımıdır. Burada amaç, ihtiyaç duyulan programı daha küçük parçalara bölerek, yönetilebilir ve yeniden kullanılabilir hale getirmektir.

Bir program/proje üretirken bunu bir sisteme oturtmak; daha anlaşılabilir, geliştirilebilir ve yönetilebilir olacaktır. Bu sistemi sağlamak için de aşağıdaki maddelere dikkat etmeliyiz:

- Kod tekrarı yapmamak
- Olabildiğince tek bir yerden yönetebiliyor olmak
- Kodun bakımını ve başkaları tarafından okunmasını kolaylaştırmak
- Spaghetti code’dan kaçınmak🙂
  
Bu yaklaşımı benimsemenin adımlarından biri OOP ‘dir. Oluşturacağımız Class(Sınıf)’lar sayesinde kod yapısını parçalara böleriz ve karmaşıklığı azaltmış oluruz. Şimdi, hayal gücümüzü kullanarak bu bahsettiklerimizi daha somut bir hale getirelim.


Programımıza, sanki yeni bir dil öğretiyormuşuz gibi, tamamen yabancı bir kavramı tanıtalım: diyelim ki bu yeni kavram bir “Kuş”. Bu kuşun bazı temel özellikleri var: Adı, Cinsi, Yaşı gibi.

Ayrıca kuşun çeşitli davranışları var: Ötmek, Uçmak gibi.


		class Kus {
		    //Properties
		    public string Ad { get; set; } 
		    public string Cins { get; set; }
		    public int Yas { get; set; }
		 
		    //Methods
		    public void Ses()
		    {
		        Console.WriteLine("Cik!");
		    }
		}


Burada ;

Kuş -> Class

Ad , Cins, Yaş gibi özellikler -> Properties (“prop” yazıp tab tuşuyla oluşturabilirsiniz)

Ses çıkarmak , Uçmak -> Methods

Artık programımız Kuş’u tanıyor. her seferinde yeni bir kuş tanımlayıp fazla kod yazmayacağız. Kuş class’ını kullanarak yeni object’ler üreteceğiz.

Not olarak: Property(özellikleri) tanımlarken tanımladığımız özelliğin veri tipini tanımlamalıyız. (String, int, double.. gibi)

Class’ı kullanabilmek için bir örneğini oluşturmak gereklidir.

Şimdi Kuş class’ından bir object üretelim(kus_). Artık “kus_” object’i üzerinden Ad, Cins, Yas ve Ses() methoduna erişebileceğiz. Programımız artık kus_’un ne olduğunu tanıyor olacak.

		static void Main(string[] args)
		  {
		    Kus kus_ = new Kus(); // new keyword'ü ile Kus classından object ürettik
		
		    // Property'lere değer atıyoruz.
		    kus_.Ad = "Pamuk"; 
		    kus_.Cins = "Papağan";
		    kus_.Yas = 3;
		
		    // Class üzerinden metodu (davranışını) çağırdık ve konsola değerleri yazdırdık
		    kus_.Ses(); 
		    Console.WriteLine($"İsim: {kus_.Ad}, Cinsi: {kus_.Cins}, Yaşı:{kus_.Yas}"); 
		    Console.ReadLine();
		   }

![image](https://github.com/dilanmetin/OOP-Nesne-Yonelimli-Programlama/assets/131908432/2e2ac4ea-c0af-4ab6-ab21-1dad0ed02955)


<b>Constructor Nedir?</b>

Constructor (yapıcı metod), bir sınıf örneği oluşturulduğunda otomatik olarak çağrılan bir metoddur. Constructor, nesnenin başlatılması için kullanılır ve genellikle sınıfın özelliklerini başlatmak ve başlangıç durumunu yapılandırmak için kullanılır. Constructor, sınıf adıyla aynı isme sahiptir. (“ctor” yazıp tab tuşuyla hızlıca oluşturabilirsiniz)

Constructorlar, parametresiz veya parametreli olabilir. Bu sefer başka bir örnek üzerinden anlayalım.

		public class Kisi
		{
		    public string Ad { get; set; }
		    public string Soyad { get; set; }
		    public int Yas { get; set; }
		
		    // Parametresiz Constructor
		    public Kisi()
		    {
		        Ad = "Dilan";
		        Soyad = "Metin";
		        Yas = 28;
		    }
		
		    // Parametreli Constructor
		    public Kisi(string ad, string soyad, int yas)
		    {
		        Ad = ad;
		        Soyad = soyad;
		        Yas = yas;
		    }
		}
		public class Program
		    {
		        static void Main(string[] args)
		        {
		            
		            Kisi kisi1 = new Kisi("Burak","İşler",27);
		            Kisi kisi2 = new Kisi();
		            Console.WriteLine($"{kisi1.Ad}, {kisi1.Soyad}, {kisi1.Yas}");
		            Console.WriteLine($"{kisi2.Ad}, {kisi2.Soyad}, {kisi2.Yas}");
		
		            Console.ReadLine();
		
		        }
		    }

![image](https://github.com/dilanmetin/OOP-Nesne-Yonelimli-Programlama/assets/131908432/3f09170f-29bf-4f5f-95c8-ed6d269f517b)

Kişi1 için Parametreli constructor kullandık object oluştururken parantez içinde değerleri girdik.
Kişi2 için Parametresiz constructor kullandık, varsayılan değerleri bize döndürdü.

=> Constructor bize ne sağladı? diye sorarsak eğer; object oluşturmak için teker teker property değerlerini girmedik tek satırda hallettik.

<b>OOP'nin 4 Temel ilkesi</b>

OOP’nin 4 temel ilkesi ; Encapsulation, Inheritance, Polymorphism ve Abstraction’ dır.

<b>1) Encapsulation (Kapsülleme)</b>: Bir class’ın verilerinin ya da değişkenlerinin class dışındaki verilerden gizlenmesidir. Sadece belirli metodlar aracılığıyla bu verilere erişim sağlanmasını sağlar. Bu şekilde dışarıdan gelen istenmeyen müdahaleleri önlemiş oluruz ve nesneler arasındaki bağımlılığı azaltırız.
→ Bu gizlemeyi “private” erişim belirteci (Access Modifiers) ile yaparız. 

Hemen aşağıda bir örneğe göz atalım. Burada doğrudan “tur” ve “renk” e erişmiyoruz. Onun yerine “Tur” ve “Renk” adında public property’ler kullanarak erişim sağlıyoruz.

			class Kus
			    {
			        private string tur;  // private değişken
			        private int dogumYili; // private değişken
			        // Tür için property
			        public string Tur
			        {
			            get { return tur; }
			            set { tur= value; }
			        }
			        // Dogumyili için property
			        public int DogumYili
			        {
			            get { return dogumYili; }
			            set { dogumYili= value; }
			        }
			        public Kus(string tur, int dogumYili)  // Constructor
			        {
			            this.Tur =tur;
			            this.DogumYili = dogumYili;
			        }
			        public int Yas() // Geri dönüş değeri int olan ve yaş hesaplayan metod
			        {
			            return DateTime.Now.Year - DogumYili;
			        }
			    }
			class Program
			{
			    static void Main(string[] args)
			    {
			         Kus kus1 = new Kus("Papağan", 2020);
			         Console.WriteLine($"Tür:{kus1.Tur}");
			         Console.WriteLine($"Yaş: {kus1.Yas()}");
			         Console.ReadLine();
			    }
			}

![image](https://github.com/dilanmetin/OOP-Nesne-Yonelimli-Programlama/assets/131908432/83c3e52f-893a-4505-8a17-f847cc70a2c6)

→ Görüldüğü gibi biz private tanımlanan değişkenlere erişemedik. Object üzerinden sadece Tur ve Yas’ı çağırabildik.

<b>2)Inheritance (Kalıtım)</b>: Bir sınıfın, başka mevcut bir sınıfın özelliklerini ve davranışlarını miras olarak alması anlamına gelir. Bu yeni sınıf (Child-Türetilmiş) Mevcut sınıfın(Parent — Base) özelliklerini ve davranışlarını yeniden kullanarak yeni bir sınıf oluşturmayı sağlar.

Miras almak için ” : “ sembolünü kullanıyoruz.

			class Kus   // Parent Sınıf
			{
			    public string tur { get; set; }
			    public string renk { get; set; }
			    public void Uc()
			    {
			        Console.WriteLine("Kuş uçuyor.");
			    }
			}
			class Serce : Kus  // Kus sınıfından türetilen bir alt sınıf (Child Sınıf)
			{
			    public void Cıvıldar()
			    {
			        Console.WriteLine("Serçe cıvıldıyor.");
			    }
			}
			class Program
			{
			    static void Main(string[] args)
			    {
			        Serce serce1 = new Serce();
			        serce1.tur= "Serçe";
			        serce1.renk= "Kahverengi";
			        Console.WriteLine("Tür: " + serce1.tur);    // Çıktı: Serçe
			        Console.WriteLine("Renk: " + serce1.renk);  // Çıktı: Kahverengi
			        serce1.Uc();        // Kuş sınıfından miras alınan metot
			        serce1.Cıvıldar();  // Serçe sınıfına özgü metot
			        Console.ReadLine();
			    }
			}

![image](https://github.com/dilanmetin/OOP-Nesne-Yonelimli-Programlama/assets/131908432/7157d582-ada4-4801-939f-2c031400df39)

→ Burada da Serçe sınıfını Kuş sınıfından türettik. Kuş sınıfında olan metotları ve property’leri miras almış olduk. Hem Kuş sınıfının property’leri olan tür ve renk’e ulaşıp tanımladık hem de Serçe’ye özgü metotları tanımlayıp object üzerinden çağırabildik.

<b>3) Polymorphism (Çok Biçimlilik)</b>: Farklı nesnelerin aynı metodları çağırabilmesi ve farklı davranışlar sergileyebilmesi anlamına gelir. Polymorphism, aynı ad altında farklı sınıfların farklı davranışlarını ifade etme yeteneğidir.

→ Polimorfizm’i Su örneği ile daha rahat anlayabiliriz. Suyun doğada 3 hali vardır; katı, sıvı ve gaz. Aslında hepsi sudur ama şekilleri farklıdır.

Aşağıdaki örnekte de Hayvan classını baz alacağız(inherit edeceğiz) ve Ses() metodunun farklı formlarını türetebileceğiz.

			  class Hayvan
			    {
			        public virtual void Ses() // virtual olarak işaretliyoruz.
			        {
			            Console.WriteLine("Hayvanlar ses çıkarır");
			        }
			        
			    }
			    class Kus : Hayvan
			    {
			        public override void Ses() // override ile Ses metodunu ezip yeni tanımlama yapabiliriz.
			        {
			            Console.WriteLine("Cik!");
			        }
			    }
			    class Ari : Hayvan
			    {
			        public override void Ses() // override ile Ses metodunu ezip yeni tanımlama yapabiliriz.
			        {
			            Console.WriteLine("Zzz!");
			        }
			    }
			    class Kopek : Hayvan
			    {
			        public override void Ses() // override ile Ses metodunu ezip yeni tanımlama yapabiliriz.
			        {
			            Console.WriteLine("Hav!");
			        }
			    }
			class Program
			{
			    static void Main(string[] args)
			    {
			        Hayvan kus= new Kus();
			        Hayvan ari= new Ari();
			        Hayvan kopek= new Kopek();
			
			        kus.Ses();  // Çıktı: Cik!
			        ari.Ses();  // Çıktı: Zzz!
			        kopek.Ses();  // Çıktı: Hav!
			        Console.ReadLine();
			        
			    }
			}

![image](https://github.com/dilanmetin/OOP-Nesne-Yonelimli-Programlama/assets/131908432/5d77b614-1d47-4ea8-80bf-cae7cf0a0cf8)

→ Bu örnekte Kuş, Köpek, Arı class’larını Hayvan class’ından inherit ettik ve hepsinde aynı Ses() metodunu alt sınıflarda farklı şekilde kullanabildik.

→ Ses metodunu ilk tanımladığımız yerde virtual olarak işaretliyoruz ve değiştirilebilir olduğunu belirtmiş oluyoruz. Daha sonra alt sınıflarda bu metodu kullanırken override yazıp asıl metodu ezmiş oluyoruz.

<b>4. Abstraction (Soyutlama)</b>: Abstraction da ise bir nesnenin önemli olan özellikleri ve fonksiyonları dışarıya sunulur, gerekli olmayan detaylar gizlenir.

Not: Abstract sınıfları, Sınıflar arasında ortak özellik ve metot olması durumunda oluştururuz.


Soyutlama, soyut sınıflar (abstract classes) ve arayüzler (interfaces) kullanılarak uygulanır. Object’lere ne yapmaları gerektiği aktarılır, nasıl yapacakları onlara bırakılır.


			// Soyut Telefon sınıfı
			public abstract class Telefon
			{
			    // propertyler
			    public string Marka { get; set; } 
			    public string Model { get; set; } 
			
			    // Abstract metodlar. Burada sadece metot tanımlarını yapıyoruz. 
			    // Nasıl yapacağını söylemiyoruz.
			    public abstract void Ac();
			    public abstract void Kapat();
			    public abstract void AramaYap(string numara);
			}
			
			// Gerçek Telefon sınıfı
			public class GercekTelefon : Telefon
			{
			    // Burada metotların nasıl yapılacağını yazıyoruz.
			    public override void Ac()
			    {
			        Console.WriteLine($"{Marka} {Model} telefonu açılıyor...");
			    }
			
			    public override void Kapat()
			    {
			        Console.WriteLine($"{Marka} {Model} telefonu kapatılıyor...");
			    }
			
			    public override void AramaYap(string numara)
			    {
			        Console.WriteLine($"{numara} numarası aranıyor...");
			    }
			
			   
			}
			
			class Program
			{
			    static void Main(string[] args)
			    {
			        Telefon telefon = new GercekTelefon();
			
			        // Telefonun özelliklerini ayarlayalım
			        telefon.Marka = "Samsung";
			        telefon.Model = "Galaxy S21";
			       
			
			        telefon.Ac();
			
			        telefon.AramaYap("05555555555");
			
			        telefon.Kapat();
			        Console.ReadLine();
			    }
			}

→ Bu örnekte ise Telefon sınıfını abstract olarak işaretledik, metod tanımlamaları yaptık. Daha sonra alt sınıfta bu metodları override ederek içini doldurduk.

![image](https://github.com/dilanmetin/OOP-Nesne-Yonelimli-Programlama/assets/131908432/db3150da-ebbb-4690-a1d1-1942bf95a4a6)


Encapsulation, Inheritance, Polymorphism ve Abstraction, nesne yönelimli programlamanın temelidir ve birlikte kullanarak kodlarımızı daha okunabilir, modüler, esnek ve sürdürülebilir olmasını sağlarız.

Ortak Faydalar:

- Kodun Daha Modüler Olması: Her dört kavram da kodun modüler olmasını sağlar. Kod blokları daha küçük parçalara bölünerek daha kolay yönetilebilir hale gelir.
- Kod Tekrarını Azaltma: Her dört kavram da kod tekrarını azaltır. Ortak özellikler ve davranışlar bir üst sınıfta tanımlanarak, alt sınıflar tarafından tekrar yazılmasına gerek kalmaz.
- Esneklik ve Genişletilebilirlik: Bu kavramlar, kodun daha esnek ve genişletilebilir olmasını sağlar. Kodun daha kolayca değiştirilebilmesi ve yeni gereksinimlere uyum sağlayabilmesi için temel yapıyı sağlarlar.
- Daha Az Hata İçermesi: Her dört kavram da kodun daha az hata içermesine yardımcı olur. Kod tekrarının azalması ve daha modüler bir yapıyla birlikte, hata yapma olasılığı azalır.


OOP, katmanlı mimari yapısında sıkça kullandığımız bir yapı. Bu yüzden ilerde daha karmaşık konuları rahat anlayabilmek adına OOP konusunu bence iyi anlamak gerekli.
Umarım sizlere yardımcı olabilmişimdir. Daha ayrıntılı bilgiler için benim de faydalandığım linkleri aşağıda paylaşıyorum♥

Yazılarım için beni medium hesabımdan takip edebilirsiniz. --> https://medium.com/@dilanmetin

— Linkler —

https://www.programiz.com/csharp-programming/class-objects

https://medium.com/kodcular/adan-z-ye-c-oop-2d766cf2d144

https://www.youtube.com/watch?v=g7If_L8KaEQ&ab_channel=Kodluyoruz

https://www.youtube.com/watch?v=pTB0EiLXUC8&ab_channel=ProgrammingwithMosh

https://medium.com/@dileepsreepathi/oops-concepts-c-e3c094bbb8cb

https://www.youtube.com/watch?v=NyW4OrFuU8g

https://www.ybsmezunu.com/c-ile-nesne-yonelimli-programlama-oop-ile-temel-kavramlar/

https://medium.com/@wdrleo/temel-oop-kavramlar%C4%B1-2cffe73245f7
