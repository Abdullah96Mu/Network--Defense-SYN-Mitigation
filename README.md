## 1. مقدمة المشروع (Project Overview):
هذا المشروع يحاكي دورة حياة الحادث الأمني (Incident Life Cycle) بشكل متكامل؛ بدءاً من الكشف عن الـ (Stealth SYN Scan)، مروراً بتحليل الحزم لعزل التهديد، وصولاً إلى تطبيق الـ (Mitigation) وتوثيق النتائج كخبير أمن سيبراني.
## 2. مرحلة الكشف (Detection Phase):
في هذة المرحلة تم استخدام اداة (Nmap) للكشف عن المنافذ المفتوحة. 
النتيجة: (Targeted Reconnaissance Identified): تم رصد محاولة مسح منافذ منظمة من العنوان '10.143.139.180' تستهدف الخدمات الحساسة.
![Nmap Stealth Scan](images/Stealth_Scan.png)
![Wireshark Detection](images/Detection_Attack.png)
## 3. إجراءات الحماية (Mitigation Steps):

أنشَأتُ قاعدة مخصصة في جدار الحماية (Windows Firewall) لحتى احظر جميع الاتصالات الواردة من الآيبي المهاجم.
  ## الصور بالاسفل تشرح خطوات انشاء قاعدة مخصصة (اختيارية)
  ![Firewall Securtiy](images/firewall_config_1.jpg)
  ![Firewall Securtiy](images/firewall_config_2.png)

 # 4. تحليل ما بعد الحظر (Post-Mitigation Analysis) 
 بعد تفعيل الحظر. تاكدت من نجاح استراتيجية الدفاع كالاتي:
النتيجة الأولى: (Increased Attacker Resource Consumption): ظهور حزم (TCP Retransmission) بكثافة عند المراقبة مما يثبت ان المهاجم استنزف موارده واانه مجبر على اعادة المحاولات دون تلقي رد من الويندوز (الضحية).
النتيجة الثانية: (Service Obfuscation): تغير حالة المنافذ في "Nmap" إلى "Filtered".
![Wireshark Retransmission](images/Firewall_Rule.png)
![Nmap Filtered Result](images/Filtered_Scan.jpg)
## 5. الخُلاصة الفنية (Technical Conclusion)
أثبتت نجاح استراتيجية الدفاع من خلال مراقبة سلوك الـ (TCP Retransmission)، حيث أدى الحظر إلى إجبار المهاجم على تكرار محاولات الاتصال دون تلقي أي استجابة من نظام ويندوز (Silent Drop).
