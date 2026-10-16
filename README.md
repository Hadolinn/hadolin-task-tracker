# GitHub Görev Takipçisi

GitHub Gist ile senkronize olan, tarayıcıda çalışan hızlı bir görev takip uygulaması.

## Özellikler

- **GitHub Gist Senkronizasyonu**: Tüm veriler GitHub hesabınızda saklanır
- **Notlar**: Her göreve detaylı not eklenebilir
- **Mini Fotoğraflar**: Sürükle-bırak ile fotoğraf ekleme, otomatik sıkıştırma
- **Gruplama**: Görevleri kategorilere ayırma ve filtreleme
- **Arama**: Anlık arama ile hızlı erişim
- **Tamamlanma Takibi**: Görevleri tamamlanmış olarak işaretleme
- **Karanlık Tema**: GitHub tarzı modern arayüz

## Kurulum ve Kullanım

### 1. GitHub Token Oluşturun

1. GitHub'da **Settings → Developer settings → Personal access tokens → Tokens (classic)** gidin
2. **Generate new token (classic)** seçeneğine tıklayın
3. `gist` yetkisini işaretleyin
4. Token'ı kopyalayın (gösterilir gösterilmez kaydedin)

### 2. Uygulamayı Açın

- `app.html` dosyasını çift tıklayarak tarayıcıda açın
- Veya bir sunucu kullanarak: `npx serve github-task-tracker/`

### 3. Bağlanın

1. Oluşturduğunuz token'ı "GitHub Personal Access Token" alanına yapıştırın
2. Eğer daha önce bir Gist oluşturduysanız Gist ID'sini girin, yoksa boş bırakın (otomatik oluşturulur)
3. **Bağlan** butonuna tıklayın

## Veri Yapısı

Tüm veriler GitHub Gist içinde `tasks.json` dosyası olarak saklanır:

```json
{
  "tasks": [
    {
      "id": "abc123",
      "title": "Görev başlığı",
      "note": "Detaylı not...",
      "group": "İş",
      "photo": "base64encodedstring...",
      "done": false,
      "created_at": "2024-01-15T10:30:00.000Z",
      "updated_at": "2024-01-15T10:30:00.000Z"
    }
  ],
  "groups": ["Genel", "İş", "Kişisel"]
}
```

## Fotoğraf Depolama

Fotoğraflar otomatik olarak 800px genişliğe sıkıştırılır ve formatı JPEG/0.7 olarak ayarlanır. Base64 olarak doğrudan Gist'e gömülür, harici servis gerekmez.

## Güvenlik

- Token ve Gist ID bilgileriniz tarayıcınızda `localStorage` olarak saklanır
- GitHub token'ı sadece `gist` yetkisiyle çalışır
- Tüm istekler HTTPS üzerinden yapılır

## Sorun Giderme

| Sorun | Çözüm |
|-------|------|
| "Yükleme hatası" | Token'ın `gist` yetkisine sahip olduğunu kontrol edin |
| "Kayıt hatası" | Gist ID'sinin doğru olduğunu kontrol edin |
| Fotoğraflar yüklenmiyor | Dosya boyutunun çok büyük olmadığından emin olun |

## Lisans

MIT
