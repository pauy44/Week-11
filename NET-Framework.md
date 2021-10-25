# การทดลองสัปดาห์ที่ 11  #
# การใช้งาน git ร่วมกับ Visual studio IDE #

## แนะนำ Dot NET Framework ##
__Dot NET Framework__ เป็น Framework ที่พัฒนามาเพื่อรองรับการสร้างซอฟต์แวร์บน platform ต่างๆ เช่น  แอพพลิเคชั่นบนระบบปฏิบัติการวินโดวส์ (Windows applications) ระบบปฏิบัติการโทรศัพท์เคลื่อนที่ (Mobile applications) โปรแกรมประยุกต์สำหรับเวบ (Web applications) คอมโพเนนท์ (Components) และ XML Web Services โดย .NET Framework จะอยู่บนสถาปัตยกรรมที่แยกชั้นจาก Kernel ของระบบปฏิบัติการอย่างชัดเจน เป็นผลให้สามารถนำ .NET Framework  ไปติดตั้งบนระบบปฏิบัติการได้หลากหลาย

## สถาปัตยกรรมของ .NET ##
<p align="center">  <img src = "./images/Fig-3.1.png"  width = "80%"> </p>
<p align="center"> <b> รูปที่ 3-1 </b> สถาปัตยกรรมของ .NET Framework</p>

.Net Framework  (อ่านว่า dot net framework) เป็น platform หนึ่ง ที่เตรียมเครื่องมือและเทคโนโลยีที่ช่วยให้เราสามารถพัฒนาแอพพลิเคชั่น ที่สามารถทำงานบนระบบปฏิบัติการต่างๆ (ได้แทบทุกระบบ) ซึ่ง .Net Framework จะประกอบด้วยองค์ประกอบหลักสองอย่างได้แก่ Common Language Runtime (CLR) และ .Net Framework Class Library. 
Common Language Runtime (CLR)
ใน .Net Framework จะมี Common Language Runtime (CLR) ทำหน้าที่จัดการสภาพแวดล้อมสำหรับรันโปรแกรมต่างๆ บน .NET โดย code ที่ทำงานภายใต้ CLR เรียกว่า Managed Code ทำหน้าที่คอยจัดการหน่วยความจำ (memory management) และจัดการเทรด (thread management) ดังนั้นโปรแกรมต่างๆ จึงไม่จำเป็นต้องกังวงเรื่องการจัดการหน่วยความจำและเรื่องการเขียนโปรแกรมแบบ multi threading  ใน .NET framework จะมี CLR คอยทำหน้าที่ร้องขอพื้นที่หน่วยความจำของระบบตามที่โปรแกรมที่เราพัฒนาขึ้นมาต้องการจะใช้ หลังจากที่โปรแกรมของเราเลิกทำงานไปแล้ว CLR  จะคืนหน่วยความจำที่ขอมานั้นกลับคืนแก่ระบบ หากไม่มี CLR คอยจัดการหน่วยความจำ (รวมทั้งทรัพยากรอื่นๆ เช่น network, ports, files, I/O,  ฯลฯ) นักพัฒนาก็ต้องเป็นผู้ดำเนินการเอง และถ้าไม่มีการจัดการอย่างเหมาะสม จะทำให้ระบบสูญเสียทรัพยากร (จากการยืมไปใช้แล้วไม่ส่งคืน) จนระบบมีทรัพยากรเหลือน้อยเกินกว่าที่จะดำรงอยู่ต่อไปได้และหยุดทำงานลงในที่สุด ข้อดีอีกประการหนึ่งของ CLR คือจะเข้ามาทำงานแทนในส่วนที่ทุกๆ โปรแกรมต้องดำเนินการกับทรัพยากรของระบบ ทำให้นักพัฒนาประหยัดเวลาที่จะต้องมาเขียนโปรแกรมในส่วนนี้ซ้ำๆ กันในทุกโครงการซอฟต์แวร์

<p align="center">  <img src = "./images/Fig-3.2.png" width = "80%"> </p>
<p align="center"> <b> รูปที่ 3-2 </b> Common Language Runtime</p>
  

โปรแกรมที่เราเขียนขึ้น (ไม่ว่าจะเป็นภาษา C#, VB.Net, J# หรืออื่นๆ ) จะถูกตัวคอมไพเลอร์แปลเป็นภาษากลางสำหรับ .NET เรียกว่า Microsoft Intermediate Language (MSIL) ซึ่งในที่สุดจะถูกแปลเป็น Native Code โดย CLR เพื่อทำงานบนระบบปฏิบัติการ ดังรูปที่ 3.3  
ในปัจจุบัน มีภาษาที่สามารถแปลเป็น MSIL ได้หลายสิบภาษา ทั้งภาษาที่ถูกสร้างโดย Microsoft เองและโดยบริษัทอื่นๆ ซึ่งสามารถนำมารันภายใต้ CLR ร่วมกันได้อย่างราบรื่น การเปิดโอกาสให้มีการใช้ระบบร่วมกันของ code ในภาษาต่างๆ จะทำให้ลดความยากลำบากในการสร้างทีมพัฒนาซอฟต์แวร์ที่จำเป็นต้องใช้ภาษาเดียวกันทั้งหมด เพราะบางภาษาอาจจะมีนักเขียนโปรแกรมเป็นจำนวนน้อยมากแต่อาจจะยังคงมีความจำเป็น เนื่องจากภาษานั้นสามารถให้ executable unit  ที่กระชับ ทำงานรวดเร็ว มีประสิทธิภาพ และประหยัดทรัพยากรของระบบ


<p align="center">  <img src = "./images/Fig-3.3.png"  width = "80%"> </p>
<p align="center"> <b> รูปที่ 3-3 </b> กระบวนการคอมไพล์โปรแกรมภาษาต่างๆ ใน .NET Framework</p>

## .Net Framework Class Library (FCL)
ไลบรารี่ FCL นี้ บางครั้งจะถูกเรียกว่า  Base Class Library ทำหน้าที่เป็นพื้นฐานคลาสสำหรับทุกๆ ชนิดข้อมูล (data type) ใน .NET ทุกภาษาโปรแกรมบน .NET จะสามารถเรียกใช้งาน Class Library นี้ได้  อาทิเช่น โปรแกรมในภาษา VB.NET จะเรียกใช้ FCL เช่นเดียวกับ C# และทุกๆ ภาษาในตระกูล .NET  แอพพลิเคชั่นที่สามารถใช้ .net class library ตัวเดียวกันได้แก่  Windows Application, Console Application, Web Application, XML Web Services และ Windows Services.
ในทางปฏิบัติแล้ว สิ่งที่นักพัฒนาต้องทำ ก็มีเพียงแค่การนำเข้า (import) BCL ไปยังโปรแกรมโค้ดของตัวเองและเรียกใช้เมธอดที่สามารถทำงานอันซับซ้อนซึ่งอยู่ภายในไลบราบารี เช่น การอ่าน-เขียนแฟ้มข้อมูล การวาดกราฟฟิกส์ การเชื่อมต่อและทำงานกับฐานข้อมูลหรือแฟ้ม XML  โดยที่ทุกๆ ภาษาใน .NET จะใช้โค้ดเดียวกัน ทำให้ไม่มีปัญหาเรื่องความเร็วของโปรแกรมในขณะรัน แม้จะเขียนด้วยภาษาที่ง่ายๆ ก็ตาม
	นอกจากที่กล่าวมาแล้ว ใน .Net framework ยังมีส่วนประกอบที่น่าสนใจอีก 2 อย่างคือ Common Type System (CTS) และ Common Language Specification (CLS)

## Common Type System (CTS)
โดยทั่วไป ภาษาโปรแกรมต่าง ๆ มักจะมีชนิดข้อมูลมาตรฐานของตนอยู่แล้ว เมื่อนำภาษาเหล่านั้นมาคอมไพล์เป็นภาษากลางใน Common Language Runtime ก็พบว่าจะมีความแตกต่างระหว่างชนิดข้อมูลของภาษานั้นๆ กับชนิดข้อมูลกลาง (Common type system) แต่ยังคงมีความเข้ากันได้ในข้อมูลขนาดต่างๆ เช่น 1, 2, 4, 8 ไบต์ เป็นต้น จึงต้องมีการเทียบ (mapping) ชนิดข้อมูลของแต่ละภาษาไปยังชนิดข้อมูลกลางของ .NET framework  เพื่อให้โปรแกรมที่ถูกแปลมาจากภาษาเหล่านั้นสามารถใช้งานข้อมูลร่วมกันได้อย่างราบรื่น ไม่มีการสูญเสียส่วนสำคัญของข้อมูล เพื่อให้เข้าใจการ mapping ให้ดูตัวอย่างจากลิงค์ต่อไปนี้ ประกอบ 
https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/built-in-types-table

### แบบฝึกหัดเสริมความเข้าใจ

``` 
ให้นักศึกษา ค้นคว้าชนิดข้อมูลในภาษาอื่นๆ ที่สามารถทำงานบน .NET ได้ 
เช่น VB.NET ,J#, F#,ฯลฯ 
พร้อมทั้งตารางสำหรับเทียบกับ common type ใน .NET 
```


ระบบชนิดข้อมูลกลาง จะรองรับการใช้งานชนิดข้อมูลพื้นฐานสองอย่างคือ Value types และ Reference types

#### Value types:
Value types เป็นชนิดข้อมูลที่บรรจุค่าต่างๆ ไว้ในตัวเอง (เช่นธนบัตรหรือเหรียญกษาปณ์ ซึ่งมีมูลค่าตามตัวเลขบนธนบัตรหรือเหรียญนั้น ๆ) โปรแกรมจะเก็บวัตถุชนิด Value types นี้ไว้บน stack ของโปรแกรมหรือไม่ก็เก็บไว้ใน structure ขนาดเล็ก ๆ โดยที่ value types สามารถเป็นได้ทั้งแบบ built-in (กำหนดมาพร้อมกับการสร้างภาษา), แบบผู้ใช้กำหนดเอง (user-defined)  หรือแบบ enumerations
#### Reference types:
Reference types เก็บค่าตำแหน่งที่อยู่ของวัตถุที่ถูกอ้างถึง โดยวัตถุนั้นต้องถูกสร้างขึ้นโดยวิธีการจองหน่วยความจำจากระบบปฏิบัติการ เช่นคำสั่ง new เป็นผลให้วัตถุนั้นถูกเก็บอยู่ใน heap แล้วนำมาผูกไว้กับตัวแปรอีกทอดหนึ่ง โดย Reference types นี้สามารถเป็นได้ทั้งชนิด self-describing types, pointer types หรือ  interface types ทั้งนี้ self-describing types อาจหมายถึง arrays หรือ class types ก็ได้   


### Common Language Specification (CLS)


<p align="center">  <img src = "./images/Fig-3.4.png"  width = "80%"> </p>
<p align="center"> <b> รูปที่ 3-4 </b> สถาปัตยกรรม .NET ตั้งแต่รุ่น 2.0 ถึง 4.5</p>

CLS จะเป็นสมาชิกของ  Common Type System และเป็นเหมือนกฏเกณฑ์ที่คอยกำหนดให้ทุกๆ ภาษาโปรแกรมใน .NET ต้องปฏิบัติตาม เพื่อให้ใช้งานข้ามภาษาได้ทั้งที่เป็นแบบ cross language inheritance และ cross language debugging 
รายละเอียดของ .NET Framework สามารถหาอ่านเพิ่มเติมได้จากแหล่งอ้างอิง
