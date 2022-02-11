# Instruction

To compile redpill bootloader with virtio, 9p and acpid.
Run tinycore-redpill loader on kvm/proxmox with at least 1GB RAM, then type these commands:

```bash

sudo ./rploader.sh clean bromolow-7.0.1-42218

sudo ./rploader.sh update now

sudo ./rploader.sh serialgen DS3615xs

./rploader.sh ext bromolow-7.0.1-42218 add https://github.com/jimmyGALLAND/redpill-ext/raw/master/acpid/rpext-index.json

find . -name "*json" -exec grep -l "jumkey/redpill-load/raw/develop/redpill-virtio" {} \; | xargs -I {} sed -i "s/jumkey\/redpill-load\/raw\/develop\/redpill-virtio/uxora-com\/rpext\/raw\/master\/virtio_9p/g" {}

sudo ./rploader.sh build bromolow-7.0.1-42218

```



# Source
https://github.com/pocopico/tinycore-redpill
https://github.com/pocopico/rp-ext
https://github.com/jimmyGALLAND/redpill-ext
