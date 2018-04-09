### DICL Internship Program 2018

สวัสดีน้องๆที่ให้ความสนใจมาฝึกงานที่บริษัท ดิจิตอล อินไซด์เดอร์ จำกัด ในปี 2018 นี้ทุกๆคนนะครับ ก่อนที่จะเข้ามาฝึกงานกับเรา พี่มีบททดสอบเล็กน้อยเพื่อวัดทักษะพื้นฐานสำหรับนักพัฒนา Mobile Developer น้องๆไม่จำเป็นต้องตอบหรือต้องรู้ทุกเรื่องในบททดสอบนี้ เพราะเรามาสามารถมาเรียนรู้กันภายหลังได้ เพียงแต่เราอยากให้น้องๆทุกคนลองทำด้วยตัวเอง ค้นคว้าเอง ทั้งหมดก็เพื่อประโยชน์ของตัวน้องๆเองและบริษัท หากใครสนใจส่งคำตอบกันมานะได้เลยนะครับ ปิดรับสมัครวันที่ 8 เมษายน 18 เวลา 23:59 น.

## 1. Code in Swift or Java / Kotlin
แบบทดสอบนี้จะดูทักษะความรู้ความเข้าใจเกี่ยวกับเรื่อง Collection เช่น Array, Dictionary เป็นต้น

ดาวน์โหลดข้อมูล [data.json](https://github.com/memogames/dicl-intern-18/blob/master/data.json) และเขียนโค้ดเพื่อหาคำตอบ
- 1.1 หาคะแนนเฉลี่ย **score** ของนักเรียน
- 1.2 แสดงชื่อและเกรดของนักเรียนที่ได้คะแนนมากว่า 70 ขึ้นไป
- 1.3 ค้นหาชื่อนักเรียนที่มีคะแนนมากที่สุดและต่ำที่สุด **score**

คำตอบ:
```
?
package ex.pkg1;

import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;
import java.util.Arrays;
import java.util.Collections;
import java.util.Iterator;
import org.json.simple.JSONObject;
import org.json.simple.parser.JSONParser;
import org.json.simple.parser.ParseException;
import org.json.simple.JSONArray;

    public static void main(String[] args) throws Exception {

        //parsing file "data.json".
        JSONParser parser = new JSONParser();

        try {
            //find "data.json".
            JSONArray ja = (JSONArray) parser.parse(new FileReader("C:\\Users\\UserONEz\\Desktop\\test\\ex.1\\src\\data.json"));

            long Average = 0, max = -100, min = 100;
            String minScore = null, maxScore = null;

            System.out.println("1.1 หาคะแนนเฉลี่ย **score** ของนักเรียน");
            //loop for data in array.
            for (Object data : ja) {
                JSONObject Datas = (JSONObject) data;
                //get all score in array.
                long Score = (long) Datas.get("score");
                Average = Average + Score;
            }
            System.out.println("ค่าเฉลี่ยคะแนนของนักเรียน = " + Average / 6);
            System.out.println();
            System.out.println(".......................................................");
            System.out.println();

            System.out.println("1.2 แสดงชื่อและเกรดของนักเรียนที่ได้คะแนนมากว่า 70 ขึ้นไป");
            System.out.println();
            for (Object data : ja) {
                JSONObject Datas = (JSONObject) data;
                //get all name in array.
                String Name = (String) Datas.get("name");
                long Score = (long) Datas.get("score");
                if (Score > 70) {
                    System.out.println("นักเรียนที่มีคะแนนมากกว่า 70 ได้แก่ : " + Name);
                }

            }
            System.out.println("......................................................");
            System.out.println();

            System.out.println("1.3 ค้นหาชื่อนักเรียนที่มีคะแนนมากที่สุดและต่ำที่สุด **score**");
            System.out.println();
            for (Object data : ja) {
                JSONObject Datas = (JSONObject) data;
                String Name = (String) Datas.get("name");
                long Score = (long) Datas.get("score");

                if (Score < min) {
                    min = Score;//find min.
                    minScore = Name;//keep name of min.
                }

                if (Score > max) {
                    max = Score;//find max.
                    maxScore = Name;//keep name of max.
                }

            }
            System.out.println("นักเรียนที่มีคะแนนมากที่สุดคือ " + maxScore);
            System.out.println("นักเรียนที่มีคะแนนต่ำที่สุดคือ " + minScore);

        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        } catch (ParseException e) {
            e.printStackTrace();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

}

```

## 2. Create Simple Mobile Application

แบบทดสอบนี้จะดูทักษะความรู้ความเข้าใจสำหรับการพัฒนาแอปพลิเคชั่น และการใช้ UI พื้นฐานของแต่ละ Platform

### Features
- GET ข้อมูล JSON จาก [movie.json](https://github.com/memogames/dicl-intern-18/blob/master/movie.json)
- แสดงรายชื่อและรูปภาพใน ListView หรือ TableView
- ผู้ใช้สามารถกดเพื่อดูข้อมูลรายละเอียดได้ในหน้าถัดไป
- ผู้ใช้สามารถแชร์ข้อมูลชื่อหนังที่สนใจให้กับเพื่อนๆได้
- ออกแบบ UI ได้ตามความต้องการ
- ใช้ Library เพิิ่มเติิมได้

### Technical
- ดาวน์โหลดข้อมูล JSON
- เครื่องมือที่ใช้ Android Studio หรือ Xcode.

## 3. Tiny Question

Q1: Firebase คืออะไร มีฟังก์ชั่นที่น้องๆชื่นชอบนอะไรบ้างและเพราะอะไร (อย่างน้อย 3 ฟังก์ชั่น)

```
Firebase คือ NoSQL cloud database ที่เก็บข้อมูลในรูปแบบของ JSON และมีการ sync ข้อมูลแบบ realtime กับทุก devices ที่เชื่อมต่อแบบอัตโนมัติในเสี้ยววินาที รองรับการทำงานเมื่อ offline(ข้อมูลจะถูกเก็บไว้ใน local จนกระทั่งกลับมา online ก็จะทำการ sync ข้อมูลให้อัตโนมัติ) รวมถึงมี Security Rules ให้เราสามารถออกแบบเงื่อนไขการเข้าถึงข้อมูลทั้งการ read และ write ได้ดังใจ ทั้ง Android, iOS และ Web

ฟังก์ชั่นที่ชอบ
1. สีของ"console"ที่ช่วยบอกสถานะเราว่าconsoleตัวไหนที่เราพึ่งอัพเดต เพิ่มหรือลบไป เช่นหากเราอัพเดตconsoleที่ถูกอัพเดตจะเป็นสีเหลือง ถ้าเพิ่มconsoleจะเป็นสีเขียว ถ้าลบconsoleจะเป็นสีแดง
2. การเพิ่มและลบ child เราสามารถเพิ่มและลบ child ได้ง่ายโดยไม่ต้องเขียนโค้ดสามารถกดบวกเพิ่มหรือกดลบได้ทันทีที่ต้องการ
3. Storage ชอบเพราะทำให้เราอัพโหลดไฟล์ต่างๆได้ง่ายขึ้น ไม่ว่าจะเป็นไฟล์ .pdf ไฟล์วิดิโอ หรือไฟล์รูปภาพ
```

Q2: REST API คืออะไร

```
วิธีในการสร้าง Web Service รูปแบบนึงที่อาศัย HTTP Method (GET, POST, PUT, DELETE) ในการทำงาน และส่งผลกลับมาในรูปแบบของ JSON หรือ XML ทำให้สามารถรับส่งข้อมูลไปมาข้าม Platform ได้ดีมากเพราะเป็นการเรียกผ่าน HTTP Protocol ที่ใช้ในการเรียกเว็บไซต์อยู่แล้ว
```

Q3: หากต้องสร้างแอปพลิเคชั่น 1 ตัว เพื่อให้รองรับทั้งระบบ iOS และ Android วิิธีไหนที่น้องๆอยากเลือกใช้พัฒนาระหว่าง Native App กับ Cross Platform และเพราะอะไร 

```
เลือก Native App เพราะ การเขียนโค้ดแบบ Native Application จะทำให้เข้าถึงฟังก์ชั่นการทำงานของแพลตฟอร์มนั้นๆได้อย่างครบถ้วนเพราะใช้ library หรือ SDK ของ OS Mobile นั้น ๆ ที่ให้มาโดยตรง
```

Q4: ถ้าให้เลือกได้ 1 บ้าน น้องๆอยากอยู่บ้านไหนระหว่าง Apple , Google และ Microsoft

```
Google
```

Q5: เวลาว่างสิ่งที่ชอบทำที่สุดคืออะไร 2 อันดับแรก

```
1.เล่นเกมส์ที่มีภาษาอังกฤษเพื่อฝึกภาษา
2.ฝึกวาดรูป
```

Q6: แอปพลิเคชั่นไหนบนมือถือที่ชอบที่สุดและเกียจที่สุดตั้งแต่เคยใช้งานมา (ไม่รวมเกมส์) เพราะอะไร

```
ชอบที่สุดคือ class room เพราะสามารถทำได้แทบทุกอย่างที่ในคอมพิวเตอร์ทำได้ ใช้งานง่ายไม่ซับซ้อน
ไม่ชอบคือ shopee หมวดหมู่ดูยากแยกไม่ชัดเจน
```

Q7: อะไรบ้างที่น้องๆคาดว่าจะได้รับในขณะที่ฝึกงานกับพวกเรา?

```
ประสบการณ์การทำงานในรูปแบบบริษัท การทำงานร่วมกับผู้อื่น และการใช้ชีวิตแบบวัยทำงาน
```

## Submitting

ให้น้องๆ fork repo นี้แล้วตอบคำถาม จากนั้นส่ง repo มาที่ อีเมลล์ memo.games@gmail.com
