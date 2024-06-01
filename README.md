## 1. Factory Constructor 
### A factory constructor in Flutter is a special type of constructor that doesn't always create a new instance of its class. Instead, it may return an existing instance or even an instance of a different class. This flexibility allows developers to control the object creation process more precisely.

For example, a factory constructor can be used to implement a singleton pattern, where only one instance of a class is allowed to exist.

class Singleton {
  static Singleton _instance;

  factory Singleton() {
    if (_instance == null) {
      _instance = Singleton._privateConstructor();
    }
    return _instance;
  }

  Singleton._privateConstructor();
}


## 2. Modal class

Creating a user model class in Flutter is a fundamental step in organizing and managing user-related data within your application. By defining a clear structure for your data, you not only improve the maintainability of your code but also enhance its readability and reusability.

1. Attributes/Properties/Fields: => These are variables that hold the state or data associated with the entity represented by the class. Each attribute typically corresponds to a characteristic of the entity.

2. Methods/Functions: => These are functions defined within the class that operate on the data or perform certain actions related to the entity. Methods encapsulate the behavior associated with the entity.

3. Constructors: => These are special methods responsible for initializing objects of the class. Constructors often set the initial values of the attributes when an object is created.

4. Access Modifiers: =>These determine the visibility or accessibility of attributes and methods from outside the class. Common access modifiers include public, private, and protected.

```
    body: SingleChildScrollView(
      child: Column(
        children: [
          ... List.generate(invoicelist.length, (index) => ListTile(
            title: Text(invoicelist[index].name!,style: TextStyle(fontSize: 28),),
            subtitle: Text(invoicelist[index].price!,style: TextStyle(fontSize:26),),
            trailing: Text(invoicelist[index].category! ,style: TextStyle(fontSize:20),),
          )),
      
        ],
      ),
    ),
    floatingActionButton: FloatingActionButton(
      onPressed: () {
        setState(() {
          invoicelist.add(InvoiceModel(name: 'vivo',price: '14,500',category: 'Mobile-y21')
          );
        });
      },
      child: Icon(Icons.add),
    ),
  );
}
}
List invoicelist=[

InvoiceModel(name: 'Oppo',price: '10,500',category: 'Mobile-A30'),
InvoiceModel(name: 'MI',price: '9,999',category: 'Mobile'),
InvoiceModel(name: 'One +',price: '1,04,000',category: 'Mobile-Note11'),
InvoiceModel(name: 'Apple Iphone',price: '1,45,000',category: 'Mobile-15 Promax'),
];
class InvoiceModel
{


String? name;
String? price;
String? category;
InvoiceModel({this.name,this.price,this.category});
}


Future <Uint8List> genratePdf(){
final pdf=pw.Document();
pdf.addPage(
    pw.Page(
  pageFormat:PdfPageFormat.a4,
      build: (Context)=>pw.Column(
        children: List.generate(invoicelist.length, (index) => pw.Text('${invoicelist[index].name!},  ${invoicelist[index].price!}   ${invoicelist[index].category!}\n\n\n',style: pw.TextStyle(fontSize: 24)),)
      )

));return pdf.save();
}


```
