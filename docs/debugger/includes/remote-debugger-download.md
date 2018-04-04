---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 273f67b997da80b27c124d3119ec0871f0a061b8
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2018
---
1.  裝置或伺服器電腦，您要偵錯 （而非執行 Visual Studio 的電腦），取得正確的版本的遠端工具。

    |版本|連結|注意|
    |-|-|-|
    |Visual Studio 2017 （最新版）|[遠端工具](https://www.visualstudio.com/downloads/?q=remote+tools#remote-tools-for-visual-studio-2017)|一律會下載符合您的裝置作業系統 （x86 或 x64） 的版本。 如果已啟用增強式的安全性模式 (Windows Server)，您必須加入新的受信任站台，如果出現提示。|
    |Visual Studio 2017 （舊版）|[遠端工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|My.VisualStudio.com 遠端工具的 Visual Studio 2017 較早的版本可用。如果出現提示，聯結的免費 Visual Studio Dev Essentials 群組或使用 Visual Studio 訂用帳戶登入識別碼。 如果已啟用增強式的安全性模式 (Windows Server)，您必須加入新的受信任站台，如果出現提示。|
    |Visual Studio 2015 Update 3|[遠端工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|如果出現提示，聯結的免費 Visual Studio Dev Essentials 群組或使用 Visual Studio 訂用帳戶登入識別碼。 如果已啟用增強式的安全性模式 (Windows Server)，您必須加入新的受信任站台，如果出現提示。|
    |Visual Studio 2015 （舊版）|[遠端工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|如果出現提示，聯結的免費 Visual Studio Dev Essentials 群組或使用 Visual Studio 訂用帳戶登入識別碼。 如果已啟用增強式的安全性模式 (Windows Server)，您必須加入新的受信任站台，如果出現提示。|
    |Visual Studio 2013|[遠端工具](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|下載 Visual Studio 2013 文件中的頁面|
    |Visual Studio 2012|[遠端工具](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|下載 Visual Studio 2012 文件中的頁面|
  
2.  在下載頁面上，選擇符合您的作業系統 (x 86、 x64 或 ARM） 版本的工具，並下載遠端工具。
  
    > [!IMPORTANT]
    >  我們建議您安裝最新的遠端工具版本符合您的 Visual Studio 版本。 不建議使用不相符的版本。 此外，您必須安裝具有相同的架構做為您想要將它安裝所在的作業系統的遠端工具。 換句話說，如果您想要偵錯遠端電腦執行 64 位元作業系統上的 32 位元應用程式，您必須在遠端電腦上安裝 64 位元版本的遠端工具。 
    >   
    >  介面 3 從 ARM 切換到 x64 架構。 無法使用的 Visual Studio 2017 ARM 版本的遠端工具。 針對 Visual Studio 2015 中，發現 ARM 版本的 Visual Studio 2015 RTW 下載中。
  
3.  當您完成下載可執行檔時，請移至下一節，並遵循安裝指示。

如果您嘗試複製到遠端電腦的遠端偵錯工具 (msvsmon.exe) 並加以執行，請注意，**遠端偵錯工具組態精靈**(**rdbgwiz.exe**) 只有在您下載時才安裝工具。 您可能需要使用此精靈進行組態更新版本中，特別是如果您想要遠端偵錯工具以服務方式執行。 如需詳細資訊，請參閱[（選擇性） 設定遠端偵錯工具當做服務](../../debugger/remote-debugging.md#bkmk_configureService)。
