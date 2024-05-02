# obs-studio-amf-tempfix AUR Package

# Update May 2nd 2024 because of changes in OBS Studio 30.1.2 I can no longer maintain this project it is too complicated for me to update the patch to work and I am trying to get AMF to be enabled in OBS by default if you want to help get the ball rolling on that I suggest you help me tell OBS devs that with this
https://ideas.obsproject.com/posts/2591/please-enable-amf-amd-hw-encoding-options-on-linux

this started out as a temp fix for the [obs-studio-amf](https://aur.archlinux.org/packages/obs-studio-amf) package
and I used the PKGBUILD from [obs-studio-av1](https://aur.archlinux.org/packages/obs-studio-av1). the goal is to build OBS with AMF hardware encoding support which the upstream obs-studio-amf packages fails to do due to inactivity. this will allow OBS Studio to be build with AMF hardware encoding support. Any Pull Request to improve this package are welcome.

regards Ozzy

I am more active on the obs-studio-amd branch of this git repo that includes the AV1 VAAPI patch from obs-studio-av1 as well as the AMF patch that alllows for AMF hardware encoding in OBS Studio. if you are interested in using an OBS patched with AV1 VAAPI and AMF encoding options the obs-studio-amd package should be good for that.

# Final Statement
my git repo was kind of messy so if you see things changing a bit I am trying to clean it up a bit
