# Smart-tools
from tkinter import *
 
class DemoListbox:
    def __init__(self, parent, title):
        self.parent = parent
 
        self.parent.title(title)
        #self.parent.geometry("600x400")
        self.parent.protocol("WM_DELETE_WINDOW", self.onKeluar)
 
        self.dataModul = (
            ["1", "python", "Pengenalan Python", "Pengenalan Dasar", "https://www.petanikode.com/python-linux/"],
            ["2", "Python", "Instalasi Python", "Cara Instalasi", "https://www.petanikode.com/python-windows/"],
            ["3", "Python", "Menjalankan Python", "Cara Penggunaan", "https://www.petanikode.com/python-file/"],
            ["4", "Python", "IDE Python", "Aplikasi Pendukung", "https://teknologi.id/insight/ide-open-source-untuk-pengembang-python/"],
            ["5", "Python", "Hello Word Python", "Sytax Dasar", "https://www.petanikode.com/python-linux/"],
            ["5", "Python", "Hello Word Python", "Python Case Sensitive", "https://www.journaldev.com/23610/python-string-equals"],
            ["5", "Python", "Hello Word", "Komentar Python", "http://www.yusaindera.com/2017/02/membuat-komentar-di-python-tutorial.html"],
            ["5", "Python", "Hello Word", "0341-567489", "https://www.petanikode.com/python-linux/"],
            ["5", "Python", "Hello Word", "0341-867855", "https://www.petanikode.com/python-linux/"],
            ["5", "Python", "Hello Word", "Tipe Data python", "https://www.petanikode.com/python-linux/"],
            ["5", "Python", "Hello Word", "Variabel Python", "https://www.petanikode.com/python-linux/"],
            ["", "Python", "Hello Word", "Operator", "https://www.petanikode.com/python-linux/"],
            ["5", "Python", "Hello Word", "Logicial Operator", "https://www.petanikode.com/python-linux/"],
            ["5", "Python", "Hello Word", "Bitwise Operator", "https://www.petanikode.com/python-linux/"],
            ["5", "Python", "Hello Word", "Indetity Operator", "https://www.petanikode.com/python-linux/"])
 
        self.aturKomponen()
        self.aturKejadian()
        self.isiListbox()
        self.isiData()
 
        self.listboxData.focus_set()
 
    def aturKejadian(self):
        self.listboxData.bind('<ButtonRelease-1>', self.onKlikLB)
        self.listboxData.bind('<KeyRelease>', self.onKlikLB)
 
    def onKlikLB(self, event=None):
        self.isiData()
 
    def isiData(self):
        indeks = self.listboxData.curselection()
        kode = int(indeks[0])
 
        
        self.entNomor.delete(0, END)
        self.entNama.delete(0, END)
        self.entReferensi.delete(0, END)
        self.entTelp.delete(0, END)
        self.entKelas.delete(0, END)
 
      
        self.entNomor.insert(END, self.dataModul[kode][0])
        self.entNama.insert(END, self.dataModul[kode][1])
        self.entReferensi.insert(END, self.dataModul[kode][2])
        self.entTelp.insert(END, self.dataModul[kode][3])
        self.entKelas.insert(END, self.dataModul[kode][4])
 
    def isiListbox(self):
        for dat in range(len(self.dataModul)):
            self.listboxData.insert(END, self.dataModul[dat][1])
 
        self.listboxData.selection_set(0)
 
    def aturKomponen(self):
        mainFrame = Frame(self.parent)
        mainFrame.pack(fill=BOTH, expand=YES)
 
        self.statusBar = Label(mainFrame, text="MODUL PYTHON",
                               relief=SUNKEN, bd=1)
        self.statusBar.pack(side=BOTTOM, fill=X)
 
        
        fr_kiri = Frame(mainFrame, bd=10)
        fr_kiri.pack(fill=BOTH, expand=YES, side=LEFT)
 
        scroll = Scrollbar(fr_kiri, orient=VERTICAL)
        self.listboxData = Listbox(fr_kiri, width=30,
                                   yscrollcommand=scroll.set)
 
        self.listboxData.pack(fill=Y, side=LEFT)
        scroll.configure(command=self.listboxData.yview)
        scroll.pack(side=LEFT, fill=Y)
         
 
        # frame_kanan
        fr_kanan = Frame(mainFrame, bd=10)
        fr_kanan.pack(fill=BOTH, expand=YES, side=RIGHT)
 
        # fr_kanan_atas
        fr_katas = Frame(fr_kanan)
        fr_katas.pack(side=TOP, expand=YES)
 
        # data Nomor
        Label(fr_katas, text='BAB').grid(
            row=0, column=0, sticky=W)
        self.entNomor = Entry(fr_katas)
        self.entNomor.grid(row=0, column=1)
 
        # data Nama
        Label(fr_katas, text='Nama Modul').grid(
            row=1, column=0, sticky=W)
        self.entNama = Entry(fr_katas)
        self.entNama.grid(row=1, column=1)
 
        # data Referensi
        Label(fr_katas, text='Materi').grid(
            row=2, column=0, sticky=W)
        self.entReferensi = Entry(fr_katas)
        self.entReferensi.grid(row=2, column=1)
 
        # data NoTelp
        Label(fr_katas, text='Pokok Bahasan').grid(
            row=3, column=0, sticky=W)
        self.entTelp = Entry(fr_katas)
        self.entTelp.grid(row=3, column=1)
 
        # data Kelas
        Label(fr_katas, text='Referensi').grid(
            row=4, column=0, sticky=W)
        self.entKelas = Entry(fr_katas)
        self.entKelas.grid(row=4, column=1)
 
        # fr_kanan_bawah
        fr_kawah = Frame(fr_kanan)
        fr_kawah.pack(side=BOTTOM, expand=YES)
 
        self.btnAwal = Button(fr_kawah, text='<<',
                                   command=self.onAwal, width=8)
        self.btnAwal.pack(side=LEFT)
         
        self.btnPrev = Button(fr_kawah, text='<',
                                   command=self.onPrev, width=8)
        self.btnPrev.pack(side=LEFT)
 
        self.btnNext = Button(fr_kawah, text='>',
                                   command=self.onNext, width=8)
        self.btnNext.pack(side=LEFT)
         
        self.btnAkhir = Button(fr_kawah, text='>>',
                                   command=self.onAkhir, width=8)
        self.btnAkhir.pack(side=LEFT)
 
    def onAwal(self, event=None):
        datIndex = self.listboxData.curselection()
 
        self.listboxData.selection_clear(int(datIndex[0]))
        self.listboxData.selection_set(0)
        self.listboxData.activate(0)
         
        self.isiData()
     
    def onPrev(self, event=None):
        datIndex = self.listboxData.curselection()
 
        if int(datIndex[0]) == 0:
            pass
        else:
            self.listboxData.selection_clear(int(datIndex[0]))
            self.listboxData.selection_set(int(datIndex[0])-1)
            self.listboxData.activate(int(datIndex[0])-1)
         
            self.isiData()
     
    def onNext(self, event=None):
        jumDat = len(self.dataModul)
        datIndex = self.listboxData.curselection()
 
        if int(datIndex[0]) == jumDat-1:
            pass
        else:
            self.listboxData.selection_clear(int(datIndex[0]))
            self.listboxData.selection_set(int(datIndex[0])+1)
            self.listboxData.activate(int(datIndex[0])+1)
         
            self.isiData()
         
    def onAkhir(self, event=None):
        jumDat = len(self.dataModul)
        datIndex = self.listboxData.curselection()
 
        self.listboxData.selection_clear(int(datIndex[0]))
        self.listboxData.selection_set(jumDat-1)
        self.listboxData.activate(jumDat-1)
         
        self.isiData()        
     
    def onKeluar(self, event=None):
        self.parent.destroy()
 
if __name__ == '__main__':
    root = Tk()
 
    aplikasi = DemoListbox(root, "Demo Listbox - Aplikasi Data di Python")
 
    root.mainloop()
