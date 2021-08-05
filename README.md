# my-mikanos

# 環境構築
Vagrant + Virtualboxを用いて環境構築を行う。  
  
VirtualboxとVagrantをインストールし、特定のファイルを用いて`curl https://raw.githubusercontent.com/lufeee/my-mikanos/master/Vagrantfile > Vagrant`を実行する。  
そのファイルの中で`vagrant up`を実行する。その後、コマンドが終了したら`vagrant reload`を行うことで環境が整う。  
  
VirtualBoxでGUIからログインする。  
Username: vagrant, Password: vagrant  

`$HOME/edk2/Conf/target.txt`の中身を以下のように変更してください。  
  
| 設定項目        | 設定値                            |
|-----------------|-----------------------------------|
| ACTIVE_PLATFORM | MikanLoaderPkg/MikanLoaderPkg.dsc |
| TARGET          | DEBUG                             |
| TARGET_ARCH     | X64                               |
| TOOL_CHAIN_TAG  | CLANG38                           |
  
その後`$HOME/edk2`内で`build`コマンドを実行してブートローダーをビルドしてください。  
`$HOME/osbook/devenv/run_qemu.sh $HOME/edk2/Buiid/MikanLoaderX64/DEBUG_CLANG38/X64/Loader.efi $HOME/mikanos/kernel/kernel.elf`
