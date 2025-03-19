# patched-Diffusion-Models-UAD
Codebase for the paper [Patched Diffusion Models for Unsupervised Anomaly Detection](https://arxiv.org/abs/2303.03758) presented at MIDL23.

![Graphical abstract](pDDPM_graph_abstract.png)
**Abstract**: 
The use of supervised deep learning techniques to detect pathologies in brain MRI scans
can be challenging due to the diversity of brain anatomy and the need for annotated data
sets. An alternative approach is to use unsupervised anomaly detection, which only requires
sample-level labels of healthy brains to create a reference representation. This reference
representation can then be compared to unhealthy brain anatomy in a pixel-wise manner
to identify abnormalities. To accomplish this, generative models are needed to create
anatomically consistent MRI scans of healthy brains. While recent diﬀusion models have
shown promise in this task, accurately generating the complex structure of the human brain
remains a challenge. In this paper, we propose a method that reformulates the generation
task of diﬀusion models as a patch-based estimation of healthy brain anatomy, using spatial
context to guide and improve reconstruction. We evaluate our approach on data of tumors
and multiple sclerosis lesions and demonstrate a relative improvement of 25.1% compared
to existing baselines.

## 🚨 New paper: Conditioned DDPMs 🚨 
We highly recommend our latest conditioned DDPMs (cDDPMs) for unsupervised anomaly detection in brain MRIs. Our new approach offers improved performance, eliminates the need for patching, and significantly enhances domain adaptation. Check out our cDDPM repository [here](https://github.com/FinnBehrendt/Conditioned-Diffusion-Models-UAD).

## Data
We use the IXI data set, the BraTS21 data set and the MSLUB data set for our experiments. 
You can download/request the data sets here:

* [IXI](https://brain-development.org/ixi-dataset/)
* [BraTS21](http://braintumorsegmentation.org/)
* [MSLUB](https://lit.fe.uni-lj.si/en/research/resources/3D-MR-MS/)

We apply several preprocessing steps to the data, including resampling to 1.0 mm, skull-stripping with HD-BET, registration to the SRI Atlas, cutting black boarders and N4 Bias correction. 

If you’d like to use our preprocessed data, we’ve made preprocessed versions of the datasets available [here](https://1drv.ms/u/c/66229029a9e95461/EVb21X1kmXxCh_xfqMNmzH8B1Rqe_wWDHYzoQuiGj94k3Q?e=wjFP6h) (approx. 37G). 

After downloading, the directory structure of <DATA_DIR> should look like this: 

    <DATA_DIR>
    ├── Train
    │   └── ixi
    │       ├── mask
    │       └── t2
    ├── Test
    │   ├── Brats21
    │   │   ├── mask
    │   │   ├── t2
    │   │   └── seg
    │   └── MSLUB
    │       ├── mask
    │       ├── t2
    │       └── seg
    ├── splits
    │   ├──  Brats21_test.csv        
    │   ├──  Brats21_val.csv   
    │   ├──  MSLUB_val.csv 
    │   ├──  MSLUB_test.csv
    │   ├──  IXI_train_fold0.csv
    │   ├──  IXI_train_fold1.csv 
    │   └── ...                
    └── ...

You should then specify the location of <DATA_DIR> in the pc_environment.env file. Additionally, specify the <LOG_DIR>, where runs will be saved. 

## Environment Set-up
To download the code type 

    git clone git@github.com:FinnBehrendt/patched-Diffusion-Models-UAD.git

In your linux terminal and switch directories via

    cd patched-Diffusion-Models-UAD

To setup the environment with all required packages and libraries, you need to install anaconda first. 

Then, run 

    conda env create -f environment.yml -n pddpm-uad

and subsequently run 

    conda activate pddpm-uad
    pip install -r requirements.txt

to install all required packages.

## Run Experiments

To run the training and evaluation of the pDDPM, simply execute 

    python run.py experiment=MIDL23_DDPM/DDPM_patched

in your terminal. 

## Citation
If you make use of our work, we would be happy if you cite it via

        @inproceedings{behrendt2024patched,
          title={Patched diffusion models for unsupervised anomaly detection in brain mri},
          author={Behrendt, Finn and Bhattacharya, Debayan and Kr{\"u}ger, Julia and Opfer, Roland and Schlaefer, Alexander},
          booktitle={Medical Imaging with Deep Learning},
          pages={1019--1032},
          year={2024},
          organization={PMLR}
        }

  




