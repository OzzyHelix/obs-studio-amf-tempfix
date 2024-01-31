# obs-studio-amf tmpfix AUR Package
# An admission
I will admit that I have no idea what I'm doing. I simply took the obs-studio-av1 package [here](https://aur.archlinux.org/packages/obs-studio-av1) and replaced the `add_ffmpeg_vaapi_av1.patch` file with the `obs-amf-patch.patch` and replaced any mention of `add_ffmpeg_vaapi_av1.patch` in the PKGBUILD with `obs-amf-patch.patch` to get obs to build with the amf patch. So I could use obs for some work. The package won't build for me as it stands right now. So I created that repo as a temp fix for anyone having the same issue and hoped that maybe it could be a solution.

this is mostly to fix issues with the package not building and dependencies breaking due to updates 
