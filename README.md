# my-mikanos

## 環境構築
Vagrant + Virtualboxを用いて環境構築を行います。  
  
VirtualboxとVagrantをインストールし、特定のファイルを用いて`curl https://raw.githubusercontent.com/lufeee/my-mikanos/master/Vagrantfile > Vagrant`を実行します。  
そのファイルの中で`vagrant up`を実行する。その後、コマンドが終了したら`vagrant reload`を行うことで環境が作成できます。  
  
VirtualBoxでGUIからログインする。  
Username: vagrant, Password: vagrant  

`$HOME/edk2/Conf/target.txt`の中身を以下のように変更してください。  
  
| 設定項目        | 設定値                            |
|-----------------|-----------------------------------|
| ACTIVE_PLATFORM | MikanLoaderPkg/MikanLoaderPkg.dsc |
| TARGET          | DEBUG                             |
| TARGET_ARCH     | X64                               |
| TOOL_CHAIN_TAG  | CLANG38                           |
  
その後、`$HOME/edk2`内で`build`コマンドを実行してブートローダーをビルドしてください。  
次に、`$HOME/mikanos/kernel`内で`make`コマンドを実行してください。  
最後に以下のコマンドを用いてqemuを起動すればOSを起動できます。  
`$HOME/osbook/devenv/run_qemu.sh $HOME/edk2/Buiid/MikanLoaderX64/DEBUG_CLANG38/X64/Loader.efi $HOME/mikanos/kernel/kernel.elf`    
