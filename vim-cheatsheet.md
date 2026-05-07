# Vim Cheatsheet — Lengkap

> **4 Mode Utama Vim:**
> - `Normal` — default saat buka vim, untuk navigasi & perintah
> - `Insert` — mengetik teks (`i` untuk masuk, `Esc` untuk keluar)
> - `Visual` — seleksi teks (`v` untuk masuk)
> - `Command` — perintah ex (`:` untuk masuk)

---

## MEMBUKA VIM (CLI)

```bash
vim file.txt              # Buka file
vim +100 file.txt         # Buka file di baris 100
vim +/TODO file.txt       # Buka file di match pertama "TODO"
vim -p file1 file2        # Buka beberapa file dalam tab
vim -O file1 file2        # Buka dalam vertical split
vim -o file1 file2        # Buka dalam horizontal split
vim -d file1 file2        # Diff mode (bandingkan 2 file)
vimdiff file1 file2       # Sama seperti vim -d
vim -R file.txt           # Read-only
view file.txt             # Read-only (alias)
vim -u NONE file.txt      # Buka tanpa .vimrc
vim --clean file.txt      # Buka tanpa config & plugin (vim 8+)
vim -c 'set number' f.txt # Jalankan perintah setelah buka
```

---

## KELUAR VIM

| Perintah | Fungsi |
|---|---|
| `:w` | Simpan tanpa keluar |
| `:wq` atau `:x` atau `ZZ` | Simpan dan keluar |
| `:q` | Keluar (gagal jika ada perubahan) |
| `:q!` atau `ZQ` | Keluar paksa, buang perubahan |
| `:wqa` | Simpan dan keluar semua tab |
| `:qa!` | Keluar paksa dari semua tab |
| `:w !sudo tee %` | Simpan file dengan sudo |

---

## NAVIGASI KURSOR (Normal Mode)

### Dasar
| Tombol | Fungsi |
|---|---|
| `h` | Gerak kiri |
| `j` | Gerak bawah |
| `k` | Gerak atas |
| `l` | Gerak kanan |
| `gj` | Gerak bawah (teks multi-baris) |
| `gk` | Gerak atas (teks multi-baris) |

### Per Kata
| Tombol | Fungsi |
|---|---|
| `w` | Lompat ke awal kata berikutnya |
| `W` | Lompat ke awal kata berikutnya (termasuk tanda baca) |
| `e` | Lompat ke akhir kata saat ini |
| `E` | Lompat ke akhir kata saat ini (termasuk tanda baca) |
| `b` | Lompat ke awal kata sebelumnya |
| `B` | Lompat ke awal kata sebelumnya (termasuk tanda baca) |
| `ge` | Lompat ke akhir kata sebelumnya |

### Per Baris
| Tombol | Fungsi |
|---|---|
| `0` | Ke awal baris |
| `^` | Ke karakter pertama non-spasi di baris |
| `$` | Ke akhir baris |
| `g_` | Ke karakter terakhir non-spasi di baris |
| `fx` | Lompat ke kemunculan karakter `x` berikutnya di baris |
| `Fx` | Lompat ke kemunculan karakter `x` sebelumnya di baris |
| `tx` | Lompat ke sebelum karakter `x` berikutnya |
| `Tx` | Lompat ke setelah karakter `x` sebelumnya |
| `;` | Ulangi perintah f/t/F/T terakhir |
| `,` | Ulangi perintah f/t/F/T terakhir (arah berlawanan) |

### Per Dokumen
| Tombol | Fungsi |
|---|---|
| `gg` | Ke baris pertama dokumen |
| `G` | Ke baris terakhir dokumen |
| `5G` atau `5gg` | Ke baris ke-5 |
| `%` | Ke kurung/bracket pasangan `() {} []` |
| `}` | Ke paragraf/blok berikutnya |
| `{` | Ke paragraf/blok sebelumnya |
| `gd` | Ke deklarasi lokal simbol di bawah kursor |
| `gD` | Ke deklarasi global simbol di bawah kursor |

### Layar
| Tombol | Fungsi |
|---|---|
| `H` | Pindah kursor ke atas layar |
| `M` | Pindah kursor ke tengah layar |
| `L` | Pindah kursor ke bawah layar |
| `zz` | Tengahkan layar ke kursor |
| `zt` | Posisikan kursor di atas layar |
| `zb` | Posisikan kursor di bawah layar |
| `Ctrl+e` | Scroll layar turun 1 baris (kursor diam) |
| `Ctrl+y` | Scroll layar naik 1 baris (kursor diam) |
| `Ctrl+f` | Scroll layar turun 1 halaman |
| `Ctrl+b` | Scroll layar naik 1 halaman |
| `Ctrl+d` | Scroll kursor & layar turun ½ halaman |
| `Ctrl+u` | Scroll kursor & layar naik ½ halaman |

> **Tip:** Prefix angka untuk mengulang. Contoh: `4j` = gerak 4 baris ke bawah, `10l` = 10 karakter ke kanan.

---

## INSERT MODE

| Tombol | Fungsi |
|---|---|
| `i` | Insert sebelum kursor |
| `I` | Insert di awal baris |
| `a` | Append setelah kursor |
| `A` | Append di akhir baris |
| `o` | Buka baris baru di bawah, masuk insert |
| `O` | Buka baris baru di atas, masuk insert |
| `ea` | Append di akhir kata |
| `Ctrl+h` | Hapus karakter sebelum kursor |
| `Ctrl+w` | Hapus kata sebelum kursor |
| `Ctrl+j` | Tambah line break di posisi kursor |
| `Ctrl+t` | Indent baris satu shiftwidth ke kanan |
| `Ctrl+d` | De-indent baris satu shiftwidth ke kiri |
| `Ctrl+n` | Auto-complete: match berikutnya |
| `Ctrl+p` | Auto-complete: match sebelumnya |
| `Ctrl+rx` | Masukkan isi register `x` |
| `Ctrl+ox` | Masuk normal mode sementara, jalankan satu perintah `x` |
| `Esc` atau `Ctrl+c` | Keluar insert mode |

---

## EDITING (Normal Mode)

### Replace
| Tombol | Fungsi |
|---|---|
| `r` | Ganti satu karakter |
| `R` | Ganti beberapa karakter sampai `Esc` |
| `ciw` | Ganti seluruh kata |
| `cw` / `ce` | Ganti dari kursor ke akhir kata |
| `cc` / `S` | Ganti seluruh baris |
| `c$` / `C` | Ganti dari kursor ke akhir baris |
| `s` | Hapus karakter dan masuk insert |

### Join, Case, Misc
| Tombol | Fungsi |
|---|---|
| `J` | Gabung baris bawah ke baris ini (dengan spasi) |
| `gJ` | Gabung baris bawah ke baris ini (tanpa spasi) |
| `g~` | Toggle case sampai motion |
| `gu` | Ubah ke lowercase sampai motion |
| `gU` | Ubah ke uppercase sampai motion |
| `~` | Toggle case karakter di bawah kursor |
| `gwip` | Reflow paragraf |
| `xp` | Transpose dua karakter (swap) |
| `.` | Ulangi perintah terakhir |

### Undo / Redo
| Tombol | Fungsi |
|---|---|
| `u` | Undo |
| `U` | Undo seluruh perubahan di baris terakhir |
| `Ctrl+r` | Redo |

---

## HAPUS (Delete/Cut)

| Tombol | Fungsi |
|---|---|
| `x` | Hapus karakter di kursor |
| `X` | Hapus karakter sebelum kursor |
| `dd` | Hapus (cut) satu baris |
| `2dd` | Hapus 2 baris |
| `dw` | Hapus dari kursor ke awal kata berikutnya |
| `diw` | Hapus kata di bawah kursor |
| `daw` | Hapus kata + spasi di sekitarnya |
| `d$` / `D` | Hapus dari kursor ke akhir baris |
| `d0` | Hapus dari kursor ke awal baris |
| `:3,5d` | Hapus baris 3 sampai 5 |
| `:.,$d` | Hapus dari baris ini ke akhir file |
| `:g/{pattern}/d` | Hapus semua baris yang mengandung pattern |
| `:g!/{pattern}/d` | Hapus semua baris yang tidak mengandung pattern |

---

## COPY & PASTE (Yank)

| Tombol | Fungsi |
|---|---|
| `yy` atau `Y` | Yank (copy) satu baris |
| `2yy` | Yank 2 baris |
| `yw` | Yank dari kursor ke awal kata berikutnya |
| `yiw` | Yank kata di bawah kursor |
| `yaw` | Yank kata + spasi di sekitarnya |
| `y$` | Yank dari kursor ke akhir baris |
| `p` | Paste setelah kursor |
| `P` | Paste sebelum kursor |
| `gp` | Paste setelah kursor, kursor pindah ke akhir teks baru |
| `gP` | Paste sebelum kursor, kursor pindah ke akhir teks baru |
| `]p` | Paste dan sesuaikan indent ke baris saat ini |

---

## INDENT

| Tombol | Fungsi |
|---|---|
| `>>` | Indent baris ke kanan 1 shiftwidth |
| `<<` | De-indent baris ke kiri 1 shiftwidth |
| `>%` | Indent blok `()` atau `{}` (kursor di kurung) |
| `<%` | De-indent blok `()` atau `{}` |
| `>ib` | Indent isi blok `()` |
| `=iB` | Re-indent isi blok `{}` |
| `3==` | Re-indent 3 baris |
| `=%` | Re-indent blok |
| `gg=G` | Re-indent seluruh file |

---

## VISUAL MODE

| Tombol | Fungsi |
|---|---|
| `v` | Masuk visual mode (karakter) |
| `V` | Masuk visual mode (baris) |
| `Ctrl+v` | Masuk visual block mode |
| `o` | Pindah ke ujung lain seleksi |
| `O` | Pindah ke sudut lain blok |
| `Esc` / `Ctrl+c` | Keluar visual mode |

### Text Objects (dipakai bersama operator di Visual atau Normal Mode)
| Tombol | Fungsi |
|---|---|
| `aw` | Satu kata (termasuk spasi) |
| `iw` | Satu kata (tidak termasuk spasi) |
| `as` | Satu kalimat |
| `is` | Dalam kalimat |
| `ap` | Satu paragraf |
| `ip` | Dalam paragraf |
| `ab` / `a(` | Blok dengan `()` |
| `ib` / `i(` | Dalam `()` |
| `aB` / `a{` | Blok dengan `{}` |
| `iB` / `i{` | Dalam `{}` |
| `at` | Blok dengan tag `<>` |
| `it` | Dalam tag `<>` |
| `a"` | Dalam double quote termasuk quote-nya |
| `i"` | Dalam double quote tanpa quote-nya |
| `a'` | Dalam single quote termasuk quote-nya |
| `i'` | Dalam single quote tanpa quote-nya |

### Perintah di Visual Mode
| Tombol | Fungsi |
|---|---|
| `>` | Indent teks ke kanan |
| `<` | Indent teks ke kiri |
| `y` | Yank teks yang dipilih |
| `d` | Hapus teks yang dipilih |
| `~` | Toggle case |
| `u` | Ubah ke lowercase |
| `U` | Ubah ke uppercase |
| `!` | Filter teks melalui command eksternal |

---

## SEARCH & REPLACE

### Search
| Tombol | Fungsi |
|---|---|
| `/pattern` | Cari ke depan |
| `?pattern` | Cari ke belakang |
| `n` | Ulangi pencarian ke depan |
| `N` | Ulangi pencarian ke belakang |
| `*` | Cari kata di bawah kursor ke depan |
| `#` | Cari kata di bawah kursor ke belakang |
| `g*` | Cari (termasuk partial match) ke depan |
| `g#` | Cari (termasuk partial match) ke belakang |
| `:noh` | Matikan highlight pencarian |
| `\vpattern` | Very magic: semua karakter non-alfanumerik dianggap regex |

### Replace (Substitute)
| Perintah | Fungsi |
|---|---|
| `:%s/lama/baru/g` | Ganti semua di seluruh file |
| `:%s/lama/baru/gc` | Ganti semua dengan konfirmasi |
| `:s/lama/baru/g` | Ganti semua di baris saat ini |
| `:5,12s/lama/baru/g` | Ganti di baris 5–12 |
| `:%s/lama/baru/gi` | Ganti semua, case-insensitive |
| `:%s/\bkata\b/baru/g` | Ganti kata utuh saja |
| `:%s/^/teks/` | Tambahkan teks di awal setiap baris |
| `:%s/$/teks/` | Tambahkan teks di akhir setiap baris |
| `:%s/\s\+$//` | Hapus trailing whitespace |

> **Konfirmasi:** `y` ganti, `n` lewati, `a` semua, `q` berhenti, `l` ganti & berhenti.

### Search di Banyak File
| Perintah | Fungsi |
|---|---|
| `:vimgrep /pattern/ **/*` | Cari pattern di semua file |
| `:cn` | Lompat ke match berikutnya |
| `:cp` | Lompat ke match sebelumnya |
| `:copen` | Buka quickfix window (daftar hasil) |
| `:cclose` | Tutup quickfix window |

---

## REGISTERS

| Tombol | Fungsi |
|---|---|
| `:reg` | Tampilkan semua isi register |
| `"xy` | Yank ke register `x` |
| `"xp` | Paste dari register `x` |
| `"+y` | Yank ke clipboard sistem |
| `"+p` | Paste dari clipboard sistem |
| `"*y` | Yank ke X11 primary selection |

**Register Spesial:**
| Register | Isi |
|---|---|
| `"0` | Yank terakhir |
| `""` | Unnamed: delete atau yank terakhir |
| `"%` | Nama file saat ini |
| `"#` | Nama file alternatif |
| `"*` | Clipboard (X11 primary) |
| `"+` | Clipboard (X11/sistem) |
| `"/` | Pola pencarian terakhir |
| `":` | Command-line terakhir |
| `".` | Teks yang terakhir di-insert |
| `"-` | Delete kecil terakhir (< 1 baris) |
| `"=` | Expression register |
| `"_` | Black hole register (buang) |

---

## MARKS

| Tombol | Fungsi |
|---|---|
| `:marks` | Tampilkan semua mark |
| `ma` | Set mark `a` di posisi kursor |
| `` `a `` | Lompat ke mark `a` (posisi exact) |
| `'a` | Lompat ke awal baris mark `a` |
| `` y`a `` | Yank dari posisi kursor ke mark `a` |
| `` `0 `` | Posisi saat Vim terakhir ditutup |
| `` `" `` | Posisi saat file terakhir diedit |
| `` `. `` | Posisi perubahan terakhir di file ini |
| ` `` ` | Posisi sebelum lompatan terakhir |
| `:jumps` | Tampilkan jump list |
| `Ctrl+i` | Lompat ke posisi lebih baru di jump list |
| `Ctrl+o` | Lompat ke posisi lebih lama di jump list |
| `:changes` | Tampilkan change list |
| `g,` | Lompat ke perubahan lebih baru |
| `g;` | Lompat ke perubahan lebih lama |

---

## MACROS

| Tombol | Fungsi |
|---|---|
| `qa` | Mulai rekam macro ke register `a` |
| `q` | Berhenti rekam macro |
| `@a` | Jalankan macro `a` |
| `@@` | Ulangi macro terakhir |
| `5@a` | Jalankan macro `a` sebanyak 5 kali |
| `:%normal @a` | Jalankan macro `a` di setiap baris |

---

## FOLDING

| Tombol | Fungsi |
|---|---|
| `zf#j` | Buat fold dari kursor sampai # baris ke bawah |
| `zf/string` | Buat fold dari kursor ke pencarian |
| `zj` | Gerak ke awal fold berikutnya |
| `zk` | Gerak ke akhir fold sebelumnya |
| `zo` | Buka fold di kursor |
| `zO` | Buka semua fold di kursor (rekursif) |
| `zm` | Lipat lebih dalam (tambah fold level) |
| `zM` | Lipat semua fold |
| `zr` | Kurangi fold level |
| `zR` | Buka semua fold |
| `za` | Toggle fold di kursor |
| `zA` | Toggle fold rekursif |
| `zd` | Hapus fold di kursor |
| `zE` | Hapus semua fold |

---

## TABS

| Perintah | Fungsi |
|---|---|
| `:tabnew` | Buka tab baru kosong |
| `:tabnew file` | Buka file di tab baru |
| `Ctrl+wT` | Pindahkan split ke tab baru |
| `gt` atau `:tabnext` | Ke tab berikutnya |
| `gT` atau `:tabprev` | Ke tab sebelumnya |
| `#gt` | Ke tab nomor # |
| `:tabm #` | Pindahkan tab ke posisi # |
| `:tabclose` | Tutup tab saat ini |
| `:tabonly` | Tutup semua tab kecuali yang aktif |
| `:tabdo command` | Jalankan command di semua tab |

---

## SPLIT WINDOW

| Perintah | Fungsi |
|---|---|
| `:sp file` | Buka file di horizontal split |
| `:vsp file` | Buka file di vertical split |
| `Ctrl+ws` | Split horizontal |
| `Ctrl+wv` | Split vertikal |
| `Ctrl+ww` | Pindah antar window |
| `Ctrl+wh` | Pindah ke window kiri |
| `Ctrl+wl` | Pindah ke window kanan |
| `Ctrl+wj` | Pindah ke window bawah |
| `Ctrl+wk` | Pindah ke window atas |
| `Ctrl+wq` | Tutup window |
| `Ctrl+w=` | Samakan ukuran semua window |
| `Ctrl+w>` | Perlebar window |
| `Ctrl+w<` | Persempitkan window |
| `Ctrl+w+` | Tingkatkan tinggi window |
| `Ctrl+w-` | Kurangi tinggi window |

---

## BUFFER

| Perintah | Fungsi |
|---|---|
| `:e file` | Edit file di buffer baru |
| `:ls` atau `:buffers` | Tampilkan semua buffer |
| `:bn` | Buffer berikutnya |
| `:bp` | Buffer sebelumnya |
| `:b#` | Ke buffer nomor # |
| `:b file` | Ke buffer berdasarkan nama file |
| `:bd` | Hapus (tutup) buffer |
| `:ball` | Buka semua buffer di split |

---

## COMPLETION (Insert Mode)

| Tombol | Fungsi |
|---|---|
| `Ctrl+n` | Auto-complete: match berikutnya |
| `Ctrl+p` | Auto-complete: match sebelumnya |
| `Ctrl+x Ctrl+f` | Complete nama file |
| `Ctrl+x Ctrl+l` | Complete baris penuh |
| `Ctrl+x Ctrl+]` | Complete berdasarkan tag |
| `Ctrl+x Ctrl+o` | Omni completion (language-aware) |
| `Ctrl+x Ctrl+v` | Complete vim command line |

---

## DIFF MODE

```bash
vimdiff file1 file2       # Buka dalam diff mode
vim -d file1 file2        # Sama
```

| Perintah | Fungsi |
|---|---|
| `]c` | Lompat ke perbedaan berikutnya |
| `[c` | Lompat ke perbedaan sebelumnya |
| `do` atau `:diffget` | Ambil perubahan dari buffer lain ke sini |
| `dp` atau `:diffput` | Kirim perubahan dari sini ke buffer lain |
| `:diffupdate` | Update highlight diff |
| `:diffoff` | Matikan diff mode |

---

## COMMAND LINE (`:` mode)

| Perintah | Fungsi |
|---|---|
| `:!command` | Jalankan shell command |
| `:r !command` | Masukkan output command ke buffer |
| `:r file` | Masukkan isi file ke buffer |
| `:.!command` | Ganti baris saat ini dengan output command |
| `:%!command` | Filter seluruh file melalui command |
| `:set option` | Set opsi vim |
| `:set nooption` | Matikan opsi |
| `:set option?` | Cek nilai opsi |
| `:set option=value` | Set nilai opsi |
| `:help keyword` | Buka help untuk keyword |
| `K` | Buka man page untuk kata di kursor |
| `Ctrl+]` | Lompat ke tag di bawah kursor |
| `:source file` | Jalankan/load script vim |
| `:mkview` | Simpan konfigurasi view |
| `:loadview` | Muat konfigurasi view |

---

## PENGATURAN BERGUNA (`:set`)

| Perintah | Fungsi |
|---|---|
| `:set number` / `:set nu` | Tampilkan nomor baris |
| `:set nonumber` | Sembunyikan nomor baris |
| `:set relativenumber` | Nomor baris relatif |
| `:set hlsearch` | Highlight hasil pencarian |
| `:set incsearch` | Pencarian inkremental (saat ketik) |
| `:set ignorecase` | Pencarian tidak case-sensitive |
| `:set smartcase` | Case-sensitive jika ada huruf kapital |
| `:set autoindent` | Auto-indent |
| `:set tabstop=4` | Lebar tab = 4 spasi |
| `:set expandtab` | Gunakan spasi, bukan tab |
| `:set shiftwidth=4` | Lebar indent = 4 spasi |
| `:set wrap` | Wrap teks panjang |
| `:set nowrap` | Jangan wrap |
| `:set syntax=on` | Aktifkan syntax highlighting |
| `:set cursorline` | Highlight baris kursor |
| `:set clipboard=unnamedplus` | Gunakan clipboard sistem |
| `:set paste` | Mode paste (nonaktifkan auto-indent) |
| `:set list` | Tampilkan karakter tersembunyi |
| `:set fileformat=unix` | Set line ending ke Unix |

---

## FILE OPERATIONS

| Perintah | Fungsi |
|---|---|
| `:w` | Simpan file |
| `:w newname.txt` | Simpan dengan nama baru |
| `:sav newname.txt` | Simpan sebagai nama baru dan edit |
| `:w >> file` | Append ke file |
| `:e!` | Reload file (buang perubahan) |
| `:e file` | Buka file lain |
| `gf` | Buka file yang namanya di bawah kursor |
| `:set ff=dos` | Konversi ke DOS line ending |
| `:e ++ff=unix` | Buka ulang file dalam format Unix |

---

## GLOBAL COMMAND

| Perintah | Fungsi |
|---|---|
| `:g/pattern/command` | Jalankan command di setiap baris yang match |
| `:g/pattern/d` | Hapus semua baris yang mengandung pattern |
| `:g!/pattern/d` | Hapus semua baris yang tidak mengandung pattern |
| `:g/pattern/y A` | Yank semua matching lines ke register A |
| `:g/^$/d` | Hapus semua baris kosong |
| `:g/pattern/p` | Print semua matching lines |
| `:v/pattern/d` | Hapus semua baris yang tidak match (`:v` = `:g!`) |

---

## MISC BERGUNA

| Tombol | Fungsi |
|---|---|
| `Ctrl+l` | Refresh/redraw layar |
| `Ctrl+g` | Tampilkan nama file dan posisi kursor |
| `ga` | Tampilkan nilai ASCII karakter di kursor |
| `g Ctrl+g` | Tampilkan info lengkap posisi kursor |
| `Ctrl+a` | Increment angka di bawah kursor |
| `Ctrl+x` | Decrement angka di bawah kursor |
| `q:` | Buka command history window |
| `q/` | Buka search history window |
| `@:` | Ulangi command terakhir |

---

## CONTOH KOMBINASI OPERATOR + MOTION

```
d2w      → hapus 2 kata ke depan
c$       → ganti dari kursor ke akhir baris
y3j      → yank 3 baris ke bawah
>5j      → indent 5 baris ke bawah
di(      → hapus semua dalam ()
ca"      → ganti semua dalam "" termasuk quote
gUiw     → uppercase seluruh kata
=ip      → re-indent paragraf
```

---

## TIPS & TRICKS

```vim
" Hapus trailing whitespace
:%s/\s\+$//e

" Hapus baris kosong duplikat
:g/^$/,/./-j

" Nomori ulang baris (setelah hapus baris)
:%s/^\d\+/\=line('.')

" Duplicate baris saat ini
yyp

" Swap dua baris
ddp

" Pindah ke awal file
gg

" Pindah ke akhir file
G

" Hapus dari kursor ke akhir file
dG

" Copy seluruh file ke clipboard
gg"+yG

" Ganti kata di bawah kursor secara interaktif
:%s/\<<C-r><C-w>\>//gc
```

---

## .VIMRC MINIMAL YANG DIREKOMENDASIKAN

```vim
set nocompatible           " Jangan kompatibel dengan vi lama
set number                 " Tampilkan nomor baris
set relativenumber         " Nomor relatif
set hlsearch               " Highlight pencarian
set incsearch              " Pencarian inkremental
set ignorecase             " Case-insensitive search
set smartcase              " Kecuali ada kapital
set autoindent             " Auto-indent
set tabstop=4              " Tab = 4 spasi
set shiftwidth=4           " Indent = 4 spasi
set expandtab              " Spasi bukan tab
set wrap                   " Wrap panjang
set cursorline             " Highlight baris aktif
set clipboard=unnamedplus  " Clipboard sistem
set undofile               " Persistent undo
set wildmenu               " Completion visual di command line
syntax on                  " Syntax highlighting
filetype plugin indent on  " Deteksi file otomatis

" Alias berguna
nnoremap <leader>w :w<CR>
nnoremap <leader>q :q<CR>
nnoremap <C-h> :noh<CR>    " Ctrl+H hapus highlight
```

---

## REFERENSI CEPAT MODE

```
Normal  →  i / a / o / O / I / A  →  Insert
Normal  →  v / V / Ctrl+v         →  Visual
Normal  →  :                      →  Command
Any     →  Esc / Ctrl+c           →  Normal
```
