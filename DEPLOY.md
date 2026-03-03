# Panduan Deploy ke Vercel

## Persiapan

1. Pastikan Anda sudah punya akun di [Vercel](https://vercel.com)
2. Install Vercel CLI (opsional):
   ```bash
   npm install -g vercel
   ```

## Cara Deploy

### Opsi 1: Deploy via Website Vercel (Recommended)

1. **Push ke GitHub:**
   - Buat repository baru di GitHub
   - Push project ini ke repository tersebut:
     ```bash
     git init
     git add .
     git commit -m "Initial commit"
     git branch -M main
     git remote add origin https://github.com/username/repo-name.git
     git push -u origin main
     ```

2. **Import ke Vercel:**
   - Login ke [vercel.com](https://vercel.com)
   - Klik "Add New" → "Project"
   - Import repository GitHub Anda
   - Vercel akan otomatis detect settings
   - Klik "Deploy"

3. **Selesai!** 
   - Vercel akan memberikan URL: `https://nama-project.vercel.app`

### Opsi 2: Deploy via CLI

1. **Login ke Vercel:**
   ```bash
   vercel login
   ```

2. **Deploy:**
   ```bash
   cd undangan-4.x
   vercel
   ```

3. **Ikuti prompt:**
   - Set up and deploy? → Yes
   - Which scope? → Pilih akun Anda
   - Link to existing project? → No
   - Project name? → (enter nama project)
   - Directory? → `./`
   - Override settings? → No

4. **Deploy production:**
   ```bash
   vercel --prod
   ```

## Update Setelah Deploy

Setiap kali ada perubahan:

**Via GitHub:**
- Push perubahan ke GitHub
- Vercel otomatis re-deploy

**Via CLI:**
```bash
vercel --prod
```

## Custom Domain (Opsional)

1. Buka project di Vercel Dashboard
2. Settings → Domains
3. Tambahkan domain Anda
4. Update DNS sesuai instruksi Vercel

## Troubleshooting

**Build Error:**
- Pastikan `npm run build:public` berhasil di local
- Cek file `vercel.json` sudah benar

**File tidak muncul:**
- Pastikan folder `public` ter-generate
- Cek `.gitignore` tidak block file penting

**API Key tidak berfungsi:**
- Pastikan `data-key` di `index.html` sudah benar
- Cek `data-url` mengarah ke API yang benar

## Catatan Penting

- Folder `public` adalah hasil build yang akan di-deploy
- Jangan edit file di folder `public` langsung
- Edit file source, lalu run `npm run build:public`
- Access key API sudah tersimpan di file HTML
