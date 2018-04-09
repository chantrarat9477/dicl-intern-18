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
/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
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

/**
 *
 * @author UserONEz
 */
public class Ex1 {

    /**
     * @param args the command line arguments
     */
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
A1:
```

Q2: REST API คืออะไร

```
A2:
```

Q3: หากต้องสร้างแอปพลิเคชั่น 1 ตัว เพื่อให้รองรับทั้งระบบ iOS และ Android วิิธีไหนที่น้องๆอยากเลือกใช้พัฒนาระหว่าง Native App กับ Cross Platform และเพราะอะไร 

```
A3:
```

Q4: ถ้าให้เลือกได้ 1 บ้าน น้องๆอยากอยู่บ้านไหนระหว่าง Apple , Google และ Microsoft

```
A4:
```

Q5: เวลาว่างสิ่งที่ชอบทำที่สุดคืออะไร 2 อันดับแรก

```
A5:
```

Q6: แอปพลิเคชั่นไหนบนมือถือที่ชอบที่สุดและเกียจที่สุดตั้งแต่เคยใช้งานมา (ไม่รวมเกมส์) เพราะอะไร

```
A6:
```

Q7: อะไรบ้างที่น้องๆคาดว่าจะได้รับในขณะที่ฝึกงานกับพวกเรา?

```
A7:
```

## Submitting

ให้น้องๆ fork repo นี้แล้วตอบคำถาม จากนั้นส่ง repo มาที่ อีเมลล์ memo.games@gmail.com
