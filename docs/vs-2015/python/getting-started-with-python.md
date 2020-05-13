---
title: 開始使用 Python |微軟文件
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 97d60fe31f838c4cc497701f4560dc426ebc1cc9
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2020
ms.locfileid: "80543980"
---
# <a name="getting-started-with-python"></a>開始使用 Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

適用於可視化工作室的 Python 工具 (PTVS) 是免費的[開源](https://github.com/Microsoft/ptvs)外掛程式,適用於 Visual Studio,具有強大的 Python 開發體驗。  
  
## <a name="python-the-language"></a>Python 語言
  
Python 是一種流行的程式設計語言,許多大學、科學家、應用腳本編寫者、臨時開發人員和專業開發人員都使用,用於應用程式、網站和雲服務。

作為程式設計語言,Python 是:
  
- 可靠的。
- 通常可用於編寫腳本快速程式、應用腳本、桌面應用、Web 伺服器、Web 服務和科學計算。
- 易於學習及良好的設計有助於撰寫高品質程式碼 (許多大學使用它作為程式設計的入門課程)。
- 靈活、支援命令式、功能化和面向物件的程式設計樣式。
- 免費且開放的原始碼。
- 在所有主要操作系統上運行良好。  
- 由許多免費、有用且設計良好的庫提供支援。  
- 由大量文件、示例和強大的開發人員社區提供支援。  

要瞭解有關該語言的更多詳細資訊,從python.org上的[初學者 Python](https://www.python.org/about/gettingstarted/)開始。

要安裝 Python[https://www.python.org/download/](https://www.python.org/download/)本身 ,請存取 。

## <a name="python-tools-for-visual-studio"></a>Python Tools for Visual Studio
  
Visual Studio 的 Python 工具(可以從[visualstudio.com](https://www.visualstudio.com/explore/python-vs)安裝)提供以下功能:  
  
- 支援多個解譯器：CPython、IronPython 及 IPython 的各種版本  
- 以隱含方式讀取 Python 程式碼資料夾結構的專案系統，您也可以明確地控制，以便清楚什麼是應用程式程式碼、測試程式碼、網頁、JavaScript、建置指令碼等等的專案系統。  
- 適用於主控台、網路、Azure、資料科學，及其他類型的專案。    
- Python 的 Azure SDK(見下文)    
- 豐富的編輯和程式碼理解功能：語法著色、所有程式碼和程式庫的自動完成、簽章說明、類別檢視、移至定義、尋找所有參考、重構等等。    
- 互動 (REPL) 視窗
- 包含資料視覺效果的 IPython。
- IronPython 和 .NET/WPF 的支援。    
- 在無 Visual Studio 專案之下進行豐富的偵錯、能夠附加至現有可執行檔、混合模式偵錯、遠端偵錯 Windows/Linux/Mac 和互動式視窗內的偵錯。   
- 程式碼剖析工具。  
- 測試工具。  
  
下列資源將協助您開始使用：

- [安裝指南](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)    
- [快速入門及深度剖析影片 (英文)](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)  
- 安裝與功能展示(27 分鐘)*(https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [文件](https://github.com/Microsoft/PTVS/wiki)  

請注意,Visual Studio 目前沒有提供使用 Python 創建獨立可執行檔的方法,這實質上是指使用嵌入式 Python 解釋器的程式。 不過，若要這樣做，Python 社群中提供多種方式，如 [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency) 中所述。 CPython 也支援在原生的應用程式中內嵌，如[使用 CPython 可內嵌的 Zip 檔案](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/)部落格文章中所述。
  
## <a name="building-ui-with-python"></a>使用 Python 編譯 UI  

使用 Python 建構 UI 的主要產品是[Qt 專案](https://www.qt.io/qt-for-application-development/),繫結為[PySide(官方綁定)(](https://wiki.qt.io/PySide)另請參考[PySide 下載](https://download.qt.io/official_releases/pyside/.))和[PyQt](https://wiki.python.org/moin/PyQt)。 目前，Visual Studio 中的 Python 支援不包含任何特定的 UI 開發工具。

## <a name="azure-sdk-for-python"></a>適用於 Python 的 Azure SDK
  
Azure SDK for Python 支援 Windows、Mac 和 Linux，可讓您更容易使用及管理 Microsoft Azure 服務。 詳細資料請參閱下列資源： 

- 若要安裝 SDK，請使用 [Python 封裝索引 (英文)](https://pypi.python.org/pypi/azure)，或遵循 Azure 文件中的[安裝 Python 和 SDK](/azure/developer/python/azure-sdk-install)。 
- [Azure SDK for Python 開發人員中心](https://azure.microsoft.com/develop/python/)中具有從安裝到具有教學課程之文件的大量說明。  一些重點如下：  
- 作法指南：
  - [儲存 Blob](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [儲存體佇列](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [儲存表](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [服務匯流排佇列](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [服務匯流主題/訂閱](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [服務管理](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

## <a name="scientific-computing"></a>科學運算

除了所有 Python 資料科學家程式庫，適用於 Visual Studio 的 Python 工具也支援 IPython 和 IPython Notebooks (可以在 Azure 中裝載)。

建議您從[加州大學爾灣分校 (英文)](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack) 取得 IPython 和科學運算程式庫 (Matplotlib、Scipy、Numpy 等等)。  
  
## <a name="see-also"></a>另請參閱  

[開始使用 PTVS:設定使用](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
[PTVS 入門可檢視化工作室:開始編碼(專案)](../python/getting-started-with-ptvs-start-coding-projects.md)
[開始使用 PTVS:編輯代碼](../python/getting-started-with-ptvs-editing-code.md)
[開始使用 PTVS:使用](../python/getting-started-with-ptvs-debugging.md)
[PTVS 開始呼試:使用](../python/getting-started-with-ptvs-interactive-python.md)
PTVS 的互動式 Python[入門:在 Azure 中建構網站](../python/getting-started-with-ptvs-building-a-website-in-azure.md)
