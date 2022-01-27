# windows_installation_hetzner

    apt update && apt install qemu-kvm -y
    wget "http://mirror.hetzner.de/bootimages/windows/SW_DVD9_Win_Server_STD_CORE_2022__64Bit_English_DC_STD_MLF_X22-74290.ISO"

 - Now get the list of all the hdd/ssd.

`lsblk -io KNAME,TYPE,SIZE,MODEL`

  Start `parted` on the desired drive (KNAME from previous command)

    parted /dev/{kname}
    mklabel gpt
    qemu-system-x86_64 -enable-kvm -smp 4 -m 8192 -boot d -cdrom SW_DVD9_Win_Server_STD_CORE_2022__64Bit_English_DC_STD_MLF_X22-74290.ISO -drive file=/dev/{kname},format=raw,media=disk -vnc :1
