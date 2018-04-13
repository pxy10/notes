## ROOT usage

### Numerical Minimization

classes involved for 1-dimension minimization:



classes involved for multi-dimension minimization:

+ [ROOT::Math::functor](https://root.cern.ch/root/html/ROOT__Math__Functor.html)

+ [ROOT::Minuit2::Minuit2Minimizer](https://root.cern.ch/root/html/ROOT__Minuit2__Minuit2Minimizer.html)


### List Directory

```cpp
// The script is used to show how to list directory via ROOT.
// Created by pxy, 04/12/2018

#include <algorithm>    // std::find
#include <vector>       // std::vector

void ListDirectory(const char* dirname = "/media/pxy10/Documents/G4Simulation/tumuty/Pulse_build/results/",
                   const char* ext = ".root")
{
    TSystemDirectory* dir = new TSystemDirectory(dirname, dirname);
    TList* files = dir->GetListOfFiles();
    if (files){
        TSystemFile* file;
        TString fname;
        TIter next(files);
        while ((file=(TSystemFile*)next())) {
            fname = file->GetName();
            if(!file->IsDirectory() && fname.EndsWith(ext))
                cout << file->GetName() << endl;
        }
    }
} 
```

### Directory

在ROOT中, 如果涉及到同时打开了多个文件, 注意Directory的变化. 通过`gDirectory->pwd()`可以print当前的directory.

```cpp
TFile* fout = new TFile(OutputFile, "RECREATE"); // current directory is OutputFile
TFile* fin = new TFile(InputFile, "READ"); // current directory is InputFile
fout->cd(); // change to directory of OutputFile
```

对于TH1的成员, 通过`SetDirectory(0)`可以设置为不依赖于directory, 从而在directory关闭之后仍可以`Draw()`.

### Save Canvas

```cpp
{
    auto c1 = new TCanvas("c1","test",10,10,600,700);
    c1->Divide(1,2);
    c1->cd(1);
    histo0->Draw("HIST");
    c1->cd(2);
    histo1->Draw("HIST");
    c1->Print("test.png");
    gPad->Print("test.png"); // Draw()`
}
