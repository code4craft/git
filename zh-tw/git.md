# 初次設定Git

現在讀者的系統已安裝了Git，讀者可能想要做一些客製化的動作。 讀者應只需要做這些工作一次。 這些設定在更新版本時會被保留下來。 讀者可藉由再度執行命令的方式再度修改這些設定。

Git附帶名為`git config`的工具，允許讀者取得及設定組態參數，可用來決定Git外觀及運作。 這些參數可存放在以下三個地方：

*	檔案 `/etc/gitconfig`： 包含給該系統所有使用者的儲存庫使用的數值。 只要讀者傳遞 --system 參數給 git config，它就會讀取或者寫入參數到這個檔案
*	檔案 `~/.gitconfig`： 給讀者自己的帳號使用。 傳遞 --global 參數給 git config，它就會讀取或者寫入參數到這個檔案。
*	儲存庫內的設定檔，也就是 `.git/config`： 僅給所在的儲存庫使用。 每個階級的設定會覆寫上一層的。 因此，`git/config`內的設定值的優先權高過`/etc/config`。

在Windows系統，Git在`$HOME`目錄(對大部份使用者來說是`C:\Documents and Settings\$USER`)內尋找`.gitconfig`。 它也會尋找`/etc/gitconfig`，只不過它是相對於Msys根目錄，取決於讀者當初在Windows系統執行Git的安裝程式時安裝的目的地。

## 設定識別資料

讀者安裝Git後首先應該做的事是指定使用者名稱及電子郵件帳號。 這一點非常重要，因為每次Git提交會使用這些資訊，而且提交後不能再被修改：

	$ git config --global user.name "John Doe"
	$ git config --global user.email johndoe@example.com

再說一次，若讀者有指定 `--global` 參數，只需要做這工作一次。 因為在此系統，不論Git做任何事都會採用此資訊。 若讀者想指定不同的名字或電子郵件給特定的專案， 只需要在該專案目錄內執行此命令，並確定未加上 `--global` 參數。

## 指定編輯器

現在讀者的識別資料已設定完畢，讀者可設定預設的文書編輯器，當Git需要讀者輸入訊息時會叫用它。 預設情況下，Git會使用系統預設的編輯器，一般來說是Vi或Vim。 若讀者想指定不同的編輯器，例如：Emacs。可執行下列指令：

	$ git config --global core.editor emacs

## 指定合併工具

另外一個對讀者來說有用的選項是設定解決合併失敗時，讀者慣用的合併工具。 假設讀者想使用vimdiff：

	$ git config --global merge.tool vimdiff

Git能接受kdiff3、tkdiff、meld、xxdiff、emerge、vimdiff、gvimdiff、ecmerge及opendiff做為合併工具。 讀者可設定自訂的工具。 詳情參考第七章。

## 檢查讀者的設定

若讀者想確認設定值，可使用 `git config --list` 命令列出所有Git能找到的設定值：

	$ git config --list
	user.name=Scott Chacon
	user.email=schacon@gmail.com
	color.status=auto
	color.branch=auto
	color.interactive=auto
	color.diff=auto
	...

讀者可能會看到同一個設定名稱出現多次，因為Git從不同的檔案讀到同一個設定名稱（例如：`/etc/gitconfig`及`~/.gitconfig`）。 在這情況下，Git會使用最後一個設定名稱的設定值。

使用者也可以下列命令 `git config` 設定名稱，檢視Git認為該設定名稱的設定值：

	$ git config user.name
	Scott Chacon
ymbol in Windows.
