# my-mikanos

## 環境構築
Vagrant + Virtualboxを用いて環境構築を行います。  
    
VirtualboxとVagrantをインストールし、  
構築したいディレクトリ内で`curl https://raw.githubusercontent.com/lufeee/my-mikanos/master/Vagrantfile > Vagrantfile`を実行します。    
そのディレクトリの中で`vagrant up`を実行する。  
その後、コマンドが終了したら`vagrant reload`を行うことで環境が作成できます。  
  
VirtualBoxでGUIからログインする。  
Username: vagrant, Password: vagrant  

内部ターミナルで以下のコマンドを用いてqemuを起動すればOSを起動できます。  
`$HOME/osbook/devenv/run_qemu.sh $HOME/edk2/Buiid/MikanLoaderX64/DEBUG_CLANG38/X64/Loader.efi $HOME/mikanos/kernel/kernel.elf`    
