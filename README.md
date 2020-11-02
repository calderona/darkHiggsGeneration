
## How to prepare the gridpacks

https://twiki.cern.ch/twiki/bin/view/CMS/QuickGuideMadGraph5aMCatNLO

CAVEAT!! normal lxplus machines runs on slc7_amd64_gcc820 architecture. You need to use lxplus6.cern.ch machines 
running on CMSSW_9_3_16

   On the cards just change the pdf to:
   
    lhapdf = pdlabel ! PDF set
    $DEFAULT_PDF_SETS = lhaid
    $DEFAULT_PDF_MEMBERS  = reweight_PDF

   On a lxplus machine (not in a release area), you can do the following:
    
    git clone git@github.com:cms-sw/genproductions.git genproductions 	
    If you need to use mg 2.6.x then do the following:
    git clone git@github.com:cms-sw/genproductions.git genproductions -b mg26x) 
    
    cd genproductions/bin/MadGraph5_aMCatNLO/

   On my lxplus I am working under: 

    /afs/cern.ch/work/c/calderon/private/GenerateMC/genproductions/bin/MadGraph5_aMCatNLO/

    Using MG5_aMC_v2_6_0 version 
 
   For creating the cards with all the mass points: 
    
    python createGridpacks_DarkHiggs_WW.py -i DarkHiggs_WW/ -n DarkHiggs

   For running the gridpacks we should do: 
   
    ./gridpack_generation.sh DarkHiggs_MonoHs_HsToWWTo2l2nu_mhs_160_mx_100_mZp_160_TuneCP5_13TeV /cards/	production/2017/13TeV/DarkHiggs_MonoHs_HsToWWTo2l2nu_mhs_160_mx_100_mZp_160_TuneCP5_13TeV



## Running in CMS CONNECT 

   Longin into: 

    ssh -Y calderon@@login-el7.uscms.org

    cd /local-scratch/calderon/

    nohup ./submit_cmsconnect_gridpack_generation.sh  DarkHiggs_MonoHs_HsToWWTo2l2nu_mhs_200_mx_100_mZp_1200_TuneCP5_13TeV cards/prodution/2017/13TeV/DarkHiggs_MonoHs_HsToWWTo2l2nu_mhs_200_mx_100_mZp_1200_TuneCP5_13TeV  > mysubmit10.debug 2>&1 &
