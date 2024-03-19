# OOP-Nesne-Yonelimli-Programlama
OOP nedir?

OOP : Object Oriented Programming, Türkçede ise; Nesne Yönelimli Programlama demektir.

OOP, Sınıf(Class) ve Nesne(Object) kavramına dayanan bir programlama yaklaşımıdır. Burada amaç, ihtiyaç duyulan programı daha küçük parçalara bölerek, yönetilebilir ve yeniden kullanılabilir hale getirmektir.

Bir program/proje üretirken bunu bir sisteme oturtmak; daha anlaşılabilir, geliştirilebilir ve yönetilebilir olacaktır. Bu sistemi sağlamak için de aşağıdaki maddelere dikkat etmeliyiz:

- Kod tekrarı yapmamak
- Olabildiğince tek bir yerden yönetebiliyor olmak
- Kodun bakımını ve başkaları tarafından okunmasını kolaylaştırmak
- Spaghetti code’dan kaçınmak🙂
- 
Bu yaklaşımı benimsemenin adımlarından biri OOP ‘dir. Oluşturacağımız Class(Sınıf)’lar sayesinde kod yapısını parçalara böleriz ve karmaşıklığı azaltmış oluruz. Şimdi, hayal gücümüzü kullanarak bu bahsettiklerimizi daha somut bir hale getirelim.


Programımıza, sanki yeni bir dil öğretiyormuşuz gibi, tamamen yabancı bir kavramı tanıtalım: diyelim ki bu yeni kavram bir “Kuş”. Bu kuşun bazı temel özellikleri var: Adı, Cinsi, Yaşı gibi.

Ayrıca kuşun çeşitli davranışları var: Ötmek, Uçmak gibi.

class Kus
{
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

1.satırda çağırdığımız metot, 2. satırda yazdığımız property’ler
Constructor Nedir?

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

Kişi1 için Parametreli constructor kullandık object oluştururken parantez içinde değerleri girdik.
Kişi2 için Parametresiz constructor kullandık, varsayılan değerleri bize döndürdü.
=> Constructor bize ne sağladı? diye sorarsak eğer; object oluşturmak için teker teker property değerlerini girmedik tek satırda hallettik.

OOP, katmanlı mimari yapısında sıkça kullandığımız bir yapı. Bu yüzden ilerde daha karmaşık konuları rahat anlayabilmek adına OOP konusunu bence iyi anlamak gerekli.
