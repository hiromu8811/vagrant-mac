# vagrant command

```
vagrant box add <name, url, or path> # Box追加
vagrant box remove <name>            # Box削除
vagrant box list                     # Box一覧
vagrant box update                   # Boxのアップデート
vagrant box prune                    # 不要になったboxの削除
vagrant init [name [url]]            # Vagrantの初期化 (Vagrantfileが作成される)
vagrant ssh                          # sshログイン
vagrant up                           # 仮想マシン起動
vagrant halt                         # 仮想マシン停止
vagrant reload                       # 仮想マシン再起動
vagrant destroy                      # 仮想マシン削除
vagrant package                      # パッケージ作成 (仮想マシンをパッケージングする(Box形式で出力))
vagrant plugin install <name>        # プラグイン追加
vagrant plugin list                  # プラグイン一覧
vagrant plugin update                # プラグインアップデート
vagrant version                      # バージョン確認
```
