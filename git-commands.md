# Git Command Line — Lengkap

---

## SETUP & KONFIGURASI

```bash
git config --global user.name "Nama Kamu"
```
Set nama pengguna secara global.

```bash
git config --global user.email "email@kamu.com"
```
Set email pengguna secara global.

```bash
git config --global core.editor "vim"
```
Set editor default (bisa diganti: nano, code, dll).

```bash
git config --list
```
Tampilkan semua konfigurasi git yang aktif.

```bash
git config --global color.ui auto
```
Aktifkan warna pada output git di terminal.

---

## INISIALISASI

```bash
git init
```
Buat repository git baru di direktori saat ini.

```bash
git init <nama-folder>
```
Buat folder baru sekaligus inisialisasi repository.

```bash
git clone <url>
```
Salin repository remote ke lokal.

```bash
git clone <url> <nama-folder>
```
Salin repository remote ke folder dengan nama tertentu.

```bash
git clone --depth 1 <url>
```
Clone hanya commit terakhir (shallow clone, lebih cepat).

---

## STATUS & INFO

```bash
git status
```
Tampilkan status file (modified, staged, untracked).

```bash
git status -s
```
Tampilkan status dalam format singkat.

```bash
git log
```
Tampilkan riwayat commit.

```bash
git log --oneline
```
Tampilkan riwayat commit satu baris per commit.

```bash
git log --oneline --graph --all
```
Tampilkan riwayat commit semua branch dalam bentuk grafik.

```bash
git log --author="Nama"
```
Filter log berdasarkan nama author.

```bash
git log --since="2 weeks ago"
```
Tampilkan commit dalam rentang waktu tertentu.

```bash
git log -p
```
Tampilkan log beserta diff setiap commit.

```bash
git log --stat
```
Tampilkan log beserta ringkasan file yang berubah.

```bash
git show <commit-hash>
```
Tampilkan detail perubahan pada commit tertentu.

```bash
git diff
```
Tampilkan perubahan yang belum di-stage.

```bash
git diff --staged
```
Tampilkan perubahan yang sudah di-stage (siap commit).

```bash
git diff <branch1>..<branch2>
```
Bandingkan perbedaan antara dua branch.

```bash
git blame <file>
```
Tampilkan siapa yang mengubah setiap baris pada file.

---

## STAGING & COMMIT

```bash
git add <file>
```
Tambahkan file ke staging area.

```bash
git add .
```
Tambahkan semua perubahan di direktori saat ini ke staging.

```bash
git add -A
```
Tambahkan semua perubahan (termasuk delete) ke staging.

```bash
git add -p
```
Tambahkan perubahan secara interaktif (pilih per potongan kode).

```bash
git commit -m "pesan commit"
```
Commit perubahan yang sudah di-stage dengan pesan.

```bash
git commit -am "pesan commit"
```
Stage semua file yang sudah dilacak sekaligus commit.

```bash
git commit --amend
```
Edit commit terakhir (pesan atau isi).

```bash
git commit --amend --no-edit
```
Tambahkan perubahan ke commit terakhir tanpa mengubah pesan.

```bash
git restore <file>
```
Batalkan perubahan pada file yang belum di-stage.

```bash
git restore --staged <file>
```
Keluarkan file dari staging area (unstage).

```bash
git reset HEAD <file>
```
Keluarkan file dari staging (cara lama, sama dengan restore --staged).

```bash
git rm <file>
```
Hapus file dari working directory dan staging.

```bash
git rm --cached <file>
```
Hapus file dari tracking git tapi tetap ada di disk.

```bash
git mv <lama> <baru>
```
Rename atau pindahkan file sekaligus memberi tahu git.

---

## BRANCH

```bash
git branch
```
Tampilkan semua branch lokal.

```bash
git branch -a
```
Tampilkan semua branch lokal dan remote.

```bash
git branch <nama-branch>
```
Buat branch baru.

```bash
git checkout <nama-branch>
```
Pindah ke branch tertentu.

```bash
git checkout -b <nama-branch>
```
Buat branch baru sekaligus pindah ke sana.

```bash
git switch <nama-branch>
```
Pindah ke branch tertentu (perintah baru, lebih jelas).

```bash
git switch -c <nama-branch>
```
Buat branch baru sekaligus pindah ke sana (perintah baru).

```bash
git branch -d <nama-branch>
```
Hapus branch yang sudah di-merge.

```bash
git branch -D <nama-branch>
```
Paksa hapus branch meskipun belum di-merge.

```bash
git branch -m <nama-lama> <nama-baru>
```
Rename branch.

```bash
git branch --merged
```
Tampilkan branch yang sudah di-merge ke branch aktif.

```bash
git branch --no-merged
```
Tampilkan branch yang belum di-merge.

---

## MERGE

```bash
git merge <nama-branch>
```
Gabungkan branch tertentu ke branch aktif.

```bash
git merge --no-ff <nama-branch>
```
Merge dengan membuat merge commit (tidak fast-forward).

```bash
git merge --squash <nama-branch>
```
Gabungkan semua commit dari branch menjadi satu sebelum commit.

```bash
git merge --abort
```
Batalkan proses merge yang sedang berlangsung (saat konflik).

```bash
git mergetool
```
Buka tool visual untuk menyelesaikan konflik merge.

---

## REBASE

```bash
git rebase <branch>
```
Terapkan ulang commit dari branch aktif di atas branch target.

```bash
git rebase -i HEAD~<n>
```
Rebase interaktif untuk mengedit, squash, atau hapus n commit terakhir.

```bash
git rebase --continue
```
Lanjutkan rebase setelah menyelesaikan konflik.

```bash
git rebase --abort
```
Batalkan proses rebase.

```bash
git rebase --skip
```
Lewati commit yang konflik selama rebase.

---

## REMOTE

```bash
git remote
```
Tampilkan daftar remote.

```bash
git remote -v
```
Tampilkan daftar remote beserta URL-nya.

```bash
git remote add <nama> <url>
```
Tambahkan remote baru.

```bash
git remote remove <nama>
```
Hapus remote.

```bash
git remote rename <lama> <baru>
```
Rename remote.

```bash
git remote set-url <nama> <url-baru>
```
Ubah URL remote.

```bash
git fetch <remote>
```
Ambil semua perubahan dari remote tanpa merge.

```bash
git fetch --all
```
Ambil perubahan dari semua remote.

```bash
git pull
```
Ambil dan merge perubahan dari remote ke branch aktif.

```bash
git pull --rebase
```
Ambil perubahan dari remote lalu rebase (bukan merge).

```bash
git push <remote> <branch>
```
Kirim commit ke branch remote.

```bash
git push -u origin <branch>
```
Kirim commit dan set upstream tracking branch.

```bash
git push --force
```
Paksa push (timpa riwayat remote). **Berbahaya di branch shared.**

```bash
git push --force-with-lease
```
Paksa push tapi aman — gagal jika remote sudah berubah sejak fetch terakhir.

```bash
git push origin --delete <branch>
```
Hapus branch di remote.

```bash
git push --tags
```
Kirim semua tag ke remote.

---

## STASH

```bash
git stash
```
Simpan perubahan yang belum di-commit ke tumpukan sementara.

```bash
git stash push -m "pesan"
```
Simpan stash dengan pesan deskriptif.

```bash
git stash list
```
Tampilkan semua stash yang tersimpan.

```bash
git stash pop
```
Terapkan stash terakhir dan hapus dari daftar.

```bash
git stash apply stash@{n}
```
Terapkan stash tertentu tanpa menghapusnya dari daftar.

```bash
git stash drop stash@{n}
```
Hapus stash tertentu.

```bash
git stash clear
```
Hapus semua stash.

```bash
git stash branch <nama-branch>
```
Buat branch baru dari stash dan terapkan stash ke sana.

---

## TAG

```bash
git tag
```
Tampilkan semua tag.

```bash
git tag <nama-tag>
```
Buat lightweight tag di commit saat ini.

```bash
git tag -a <nama-tag> -m "pesan"
```
Buat annotated tag dengan pesan.

```bash
git tag -a <nama-tag> <commit-hash>
```
Buat tag di commit tertentu.

```bash
git show <nama-tag>
```
Tampilkan detail tag.

```bash
git tag -d <nama-tag>
```
Hapus tag lokal.

```bash
git push origin <nama-tag>
```
Kirim tag tertentu ke remote.

```bash
git push origin --tags
```
Kirim semua tag ke remote.

```bash
git push origin --delete <nama-tag>
```
Hapus tag di remote.

---

## RESET & REVERT

```bash
git reset --soft HEAD~1
```
Batalkan commit terakhir, perubahan tetap di staging.

```bash
git reset --mixed HEAD~1
```
Batalkan commit terakhir, perubahan kembali ke working directory (default).

```bash
git reset --hard HEAD~1
```
Batalkan commit terakhir, perubahan dihapus permanen. **Hati-hati!**

```bash
git reset --hard <commit-hash>
```
Kembalikan repository ke keadaan commit tertentu. **Hati-hati!**

```bash
git revert <commit-hash>
```
Buat commit baru yang membatalkan perubahan commit tertentu (aman untuk shared branch).

```bash
git revert HEAD
```
Batalkan commit terakhir dengan cara yang aman.

---

## CHERRY-PICK

```bash
git cherry-pick <commit-hash>
```
Terapkan commit tertentu dari branch lain ke branch aktif.

```bash
git cherry-pick <hash1>..<hash2>
```
Terapkan range commit ke branch aktif.

```bash
git cherry-pick --no-commit <commit-hash>
```
Terapkan perubahan tanpa langsung commit.

```bash
git cherry-pick --abort
```
Batalkan proses cherry-pick yang sedang berlangsung.

---

## SUBMODULE

```bash
git submodule add <url> <path>
```
Tambahkan repository lain sebagai submodule.

```bash
git submodule init
```
Inisialisasi submodule setelah clone.

```bash
git submodule update
```
Update submodule ke commit yang direferensikan.

```bash
git submodule update --init --recursive
```
Inisialisasi dan update semua submodule secara rekursif.

```bash
git submodule foreach git pull origin main
```
Pull update di setiap submodule.

---

## BISECT (DEBUG)

```bash
git bisect start
```
Mulai sesi bisect untuk mencari commit yang menyebabkan bug.

```bash
git bisect bad
```
Tandai commit saat ini sebagai buruk (ada bug).

```bash
git bisect good <commit-hash>
```
Tandai commit tertentu sebagai baik (belum ada bug).

```bash
git bisect reset
```
Akhiri sesi bisect dan kembali ke HEAD.

---

## WORKTREE

```bash
git worktree add <path> <branch>
```
Checkout branch ke folder lain tanpa mengganggu working directory utama.

```bash
git worktree list
```
Tampilkan semua worktree aktif.

```bash
git worktree remove <path>
```
Hapus worktree.

---

## REFLOG

```bash
git reflog
```
Tampilkan semua pergerakan HEAD (termasuk yang sudah direset). Berguna untuk recovery.

```bash
git reflog show <branch>
```
Tampilkan reflog untuk branch tertentu.

---

## CLEAN

```bash
git clean -n
```
Tampilkan file untracked yang akan dihapus (dry run).

```bash
git clean -f
```
Hapus file untracked dari working directory.

```bash
git clean -fd
```
Hapus file dan folder untracked.

```bash
git clean -fx
```
Hapus file untracked termasuk yang ada di .gitignore.

---

## SHORTLOG & STATISTIK

```bash
git shortlog -sn
```
Tampilkan jumlah commit per author, diurutkan.

```bash
git count-objects -vH
```
Tampilkan ukuran database objek git.

```bash
git ls-files
```
Tampilkan semua file yang dilacak git.

---

## .GITIGNORE

```bash
# Buat file .gitignore
touch .gitignore
```
File ini berisi pola nama file/folder yang tidak ingin dilacak git.

```bash
git check-ignore -v <file>
```
Cek apakah file diabaikan dan aturan mana yang berlaku.

```bash
git rm -r --cached .
git add .
git commit -m "fix: update .gitignore"
```
Terapkan ulang aturan .gitignore ke file yang sudah terlanjur dilacak.

---

## ALIAS BERGUNA

```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.lg "log --oneline --graph --all --decorate"
git config --global alias.undo "reset --soft HEAD~1"
```
Buat shortcut untuk perintah yang sering dipakai.

---

## TIPS

| Situasi | Perintah |
|---|---|
| Batalkan commit terakhir (aman) | `git revert HEAD` |
| Batalkan commit terakhir (lokal) | `git reset --soft HEAD~1` |
| Simpan pekerjaan sementara | `git stash` |
| Lihat siapa yang ubah baris ini | `git blame <file>` |
| Cari commit yang bikin bug | `git bisect start` |
| Pulihkan commit yang terhapus | `git reflog` |
| Sync fork dengan upstream | `git fetch upstream && git rebase upstream/main` |
