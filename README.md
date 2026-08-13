# 🤖 CrewAI Multi-Agent Workflow Lab

Bu proje, CrewAI ve Groq (Llama 3.1 8B) altyapısını kullanarak çoklu ajan (Multi-Agent) mimarilerini ve orkestrasyon desenlerini (Orchestration Patterns) pratik etmek amacıyla geliştirilmiştir.

## 📌 Proje Özeti
Sistem, belirli bir konu başlığı üzerinde otonom olarak iş birliği yapan 3 farklı uzmandan (Agent) oluşmaktadır:
1. **Kıdemli Araştırmacı:** Konu hakkında temel bulguları ve teknik detayları toplar.
2. **Teknik İçerik Yazarı:** Araştırma notlarını alır ve akıcı bir blog yazısına dönüştürür (Prompt Chaining).
3. **Baş Editör:** Hazırlanan yazıyı imla, akıcılık ve teknik doğruluk açısından denetleyip nihai hali sunar.

## 🎯 Öğrenilen ve Uygulanan Kavramlar
- **Orkestrasyon Desenleri:** Chaining (Zincirleme), Sequential Process (Sıralı İş Akışı) ve Orchestrator-Worker yapısı.
- **Agent Tasarımı:** role, goal ve backstory ile özelleştirilmiş system prompt yapılandırmaları.
- **Function Calling & Tool Use:** crewai-tools (SerperDevTool) ile canlı web araması yapabilen dinamik ajan mimarisi.
- **Observability:** Çoklu ajan sistemlerinde izlenebilirlik, hata yönetimi (self-correction) ve maliyet/latency optimizasyon esasları.

## 🛠️ Kurulum ve Çalıştırma

### 1. Gerekli Paketlerin Yüklenmesi
```bash
pip install "crewai[litellm]" crewai-tools
```
### 2. Ortam Değişkeni (Groq API Key)
Google Colab Secrets üzerinden GROQ_API_KEY tanımlandıktan sonra anahtar çekilir:
```bash
import os
from google.colab import userdata

os.environ["GROQ_API_KEY"] = userdata.get('GROQ_API_KEY')
```
### 3. Çalıştırma
Colab ortamındaki asenkron olay döngüsü (event loop) çakışmalarını önlemek için await crew.kickoff_async() ile asenkron tetiklenir.

## 🚀 Örnek Çıktı
Sistem "RAG sistemlerinde chunking" konusunu girdi olarak alıp tüm ajanlar arası veri aktarımını otomatik sağlayarak yayınlanmaya hazır nihai bir teknik blog yazısı üretmektedir.
