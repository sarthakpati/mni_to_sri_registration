# mni_to_sri_registration

Details needed to affinely register images previously registered in the MNI space to the SRI atlas.

## Requirements

[Cancer Imaging Phenomics Toolkit (CaPTk)](https://github.com/CBICA/CaPTk/) installed on your machine.

Find CaPTk's install directory, `${CaPTk_install_dir}`: https://cbica.github.io/CaPTk/FAQ.html#gs_FAQ_3

## Command to run

### For images
```powershell
git clone https://github.com/sarthakpati/mni_to_sri_registration.git /path/to/mni_to_sri_registration
cd ${CaPTk_install_dir}
./Preprocessing \ # add ".exe" for windows
  -reg Rigid # rigid transform to be applied
  -rIS 1 # save intermediate files
  -rIA /path/to/mni_to_sri_registration/affine_mniTOsri_NMI.mat # pre-computed atlas
  -rFI /path/to/mni_to_sri_registration/sri.nii.gz # sri atlas
  -i /path/to/image/to/register.nii.gz # input image
  -o /path/to/image_to_sri.nii.gz # output image
```

### For masks/segmentations/labels
```powershell
git clone https://github.com/sarthakpati/mni_to_sri_registration.git /path/to/mni_to_sri_registration
cd ${CaPTk_install_dir}
./Preprocessing \ # add ".exe" for windows
  -reg Rigid # rigid transform to be applied
  -rIS 1 # save intermediate files
  -rSg 1 # this performs segmentation-specific interpolation
  -rIA /path/to/mni_to_sri_registration/affine_mniTOsri_NMI.mat # pre-computed atlas
  -rFI /path/to/mni_to_sri_registration/sri.nii.gz # sri atlas
  -i /path/to/image/to/register_mask.nii.gz # input image
  -o /path/to/image_mask_to_sri.nii.gz # output image
```
