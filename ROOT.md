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
