# PiRacer
## Install Software On Donkeycar (Raspberry Pi OS Bookworm (64 bit))
    Step 1: Install Raspberry Pi OS Bookworm (64 bit)
    Step 2: Update and Upgrade
        sudo apt-get update --allow-releaseinfo-change
        sudo apt-get upgrade
    Step 3: Raspi-config
        sudo raspi-config
        - Enable Interfacing Options - I2C
        - Select Advanced Options - Expand Filesystem so you can use your whole sd-card storage
        - Do not enable the legacy camera (it's disabled by default, so don't change anything)
        - Choose <Finish> and hit enter.
    Step 4: Setup virtual environment
        python3 -m venv env --system-site-packages
        echo "source ~/env/bin/activate" >> ~/.bashrc
        source ~/.bashrc
        sudo apt install libcap-dev libhdf5-dev libhdf5-serial-dev
    Step 5: Install Donkeycar Python Code
        User Install (preferred way)
            pip install donkeycar[pi]
        Developer Install (only required if you want to checkout different forks, branches, tags)
            mkdir projects
            cd projects
            git clone https://github.com/autorope/donkeycar
            cd donkeycar
            git checkout main
            pip install -e .[pi]
    Further steps
        Make sure your camera works
            rpicam-hello
        Make sure tensorflow works
            python -c "import tensorflow; print(tensorflow.__version__)"

## Install Software on Host PC
