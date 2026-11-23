# Ev Enerji Sərfiyyatı və Sensor Məlumatlarının EDA Analizi

## Dataset və Sütun Qrupları
- *Fayl:* energydata_complete.csv
- *Əsas qruplar:*
  - energy_cols: appliances, lights
  - temp_cols: t1–t9 (daxili temperatur sensorları)
  - humidity_cols: rh_1–rh_9 (daxili rütubət sensorları)
  - weather_cols: t_out, press_mm_hg, rh_out, windspeed, visibility, tdewpoint

## İstifadə olunan alətlər
- *Dil:* Python
- *Kitabxanalar:* pandas, matplotlib, seaborn
- *Mühit:* Jupyter Notebook / VS Code

## Əsas analiz mərhələləri
1. *Zaman dinamikası:* Saatlıq (0–23), iş günləri vs həftəsonu və aylıq sərfiyyat dəyişikliklərinin təhlili.
2. *Paylanma və outlier analizi:* describe(), boxplot və IQR yanaşması ilə kəskin sıçrayışların araşdırılması.
3. *Korrelyasiya analizi:* heatmap vasitəsilə enerji, hava və otaq göstəriciləri arasındakı xətti əlaqələrin qiymətləndirilməsi.

## Əsas nəticələr
- *appliances paylanması sağa meyillidir:* Sərfiyyatın böyük hissəsi 40–100 aralığında paylanıb, nadir hallarda 1000 civarına çatan kəskin outlier-lar var.
- *lights dəyərləri əsasən 0-da cəmlənir:* Müşahidələrin böyük hissəsi 15.000+ sətrdə 0-da toplanır, qalan hallarda isə əsasən 10–30 aralığında müşahidə olunur.
- *Daxili otaq temperaturları (t1–t5, t7–t9) oxşar səviyyədədir (~18–22°C):* t6 sensorunun ortalaması isə kəskin fərqli olaraq xeyli aşağıdır (~7–8°C), çünki xarici mühit/çöl təsirinə daha açıqdır.
- *Saatlıq dinamika:* Həm appliances, həm də lights sərfiyyatı gecə/səhər erkən saatlarda minimumda olur, axşam saatlarında (~18:00–20:00) isə pik nöqtəyə çatır.
- *İş günləri vs Həftəsonu:* appliances sərfiyyatı həftəsonu günorta/gündüz saatlarında daha yüksək olur, axşam pikində isə hər iki qrup yüksəlir; lights isə axşam saatlarında (~18:00–21:00) daha yüksək səviyyəyə qalxır.
- *Aylıq dinamika (1–5-ci aylar):* Orta appliances sərfiyyatı 2-ci ayda (~101 civarında) pik həddə çatır, 3-cü ayda enir, 4-cü ayda qismən artıb 5-ci ayda (~93.5 civarında) ən aşağı səviyyəyə düşür.
- *Enerji və hava korrelyasiyası:* appliances ən çox lights (+0.20) ilə zəif müsbət, rh_out (-0.15) ilə zəif mənfi əlaqə göstərir; hava parametrləri arasında isə t_out ilə tdewpoint (şeh nöqtəsi) (+0.79) güclü müsbət, t_out ilə rh_out (-0.57) isə əks əlaqədədir.
- *Enerji, hava və rütubətlilik əlaqələri:* appliances-in həm hava parametrləri, həm də daxili rütubət sensorları (rh_1–rh_9) ilə xətti korrelyasiyası zəifdir; daxili rütubət sensorları öz aralarında güclü müsbət əlaqədədir, rh_6 isə rh_out (+0.72) ilə yaxınlaşıb t_out (-0.64) ilə əks əlaqə göstərir.
- *Saatlara görə paylanma və outlier-lar:* Günün bütün saatlarında yuxarı istiqamətdə kəskin sıçrayışlar (outlier-lar) mövcuddur; qutuların yayılması və ən yüksək kənar nöqtələr xüsusilə axşam saatlarında (~17:00–19:00 aralığında, maksimum 1000-dən yuxarı səviyyələrdə) daha qabarıqdır.

## Layihəni işə salmaq
1. Layihə qovluğunu kompüterinizə endirin (və ya repozitoriyanı klonlayın):
   ```bash
   git clone [repozitoriya-linki]