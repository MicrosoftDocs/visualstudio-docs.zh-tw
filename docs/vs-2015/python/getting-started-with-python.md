---
title: 開始使用 Python |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 9c18ae2731d92e6d128d13e7687bac77ae76dc8a
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59648443"
---
# <a name="getting-started-with-python"></a>開始使用 Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Python Tools for Visual Studio (PTVS)，是免費，[開放原始碼](https://github.com/Microsoft/ptvs)plug-in for Visual Studio 的強大的 Python 開發體驗。  
  
## <a name="python-the-language"></a>Python 語言
  
Python 是受歡迎的程式設計語言，可由許多大學、 科學家、 應用程式指令碼撰寫人員、 業餘開發人員和專業開發人員，處理應用程式、 網站和雲端服務。

做為程式設計語言中，Python 是：
  
- 可靠的。
- 通常適用於指令碼快速的程式、 指令碼應用程式、 傳統型應用程式、 web 伺服器、 web 服務和科學運算。
- 易於學習及良好的設計有助於撰寫高品質程式碼 (許多大學使用它作為程式設計的入門課程)。
- 有彈性，支援命令式、 功能和物件導向程式設計的樣式。
- 免費且開放的原始碼。
- 在所有主流作業系統上順利執行。  
- 支援許多免費、 有用且設計良好的程式庫。  
- 支援大量文件、 範例和強大的開發人員社群。  

若要深入了解語言，著手[適用於初學者的 Python](https://www.python.org/about/gettingstarted/) python.org 上。

若要安裝 Python，請瀏覽[ https://www.python.org/download/ ](https://www.python.org/download/)。

## <a name="python-tools-for-visual-studio"></a>Python Tools for Visual Studio
  
Python Tools for Visual Studio 中，您可以從安裝[visualstudio.com](https://www.visualstudio.com/explore/python-vs)，提供下列功能：  
  
- 支援多個解譯器：CPython、IronPython 及 IPython 的各種版本  
- 以隱含方式讀取 Python 程式碼資料夾結構的專案系統，您也可以明確地控制，以便清楚什麼是應用程式程式碼、測試程式碼、網頁、JavaScript、建置指令碼等等的專案系統。  
- 適用於主控台、網路、Azure、資料科學，及其他類型的專案。    
- Azure SDK for Python （請參閱下文）    
- 豐富的編輯和程式碼理解功能：語法著色、所有程式碼和程式庫的自動完成、簽章說明、類別檢視、移至定義、尋找所有參考、重構等等。    
- 互動 (REPL) 視窗
- 包含資料視覺效果的 IPython。
- IronPython 和 .NET/WPF 的支援。    
- 在無 Visual Studio 專案之下進行豐富的偵錯、能夠附加至現有可執行檔、混合模式偵錯、遠端偵錯 Windows/Linux/Mac 和互動式視窗內的偵錯。   
- 程式碼剖析工具。  
- 測試工具。  
  
下列資源將協助您開始使用：

- [安裝指南 (英文)](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)    
- [快速入門及深度剖析影片 (英文)](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)  
- 安裝和功能示範 （27 分鐘）] (https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [文件](https://github.com/Microsoft/PTVS/wiki)  

請注意，Visual Studio 不在目前提供方法來建立獨立的可執行檔使用 Python，這基本上表示內嵌的 Python 解譯器的程式。 不過，若要這樣做，Python 社群中提供多種方式，如 [StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency) 中所述。 CPython 也支援在原生的應用程式中內嵌，如[使用 CPython 可內嵌的 Zip 檔案](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/)部落格文章中所述。
  
## <a name="building-ui-with-python"></a>建置 UI，使用 Python  

主要供應項目建置 UI，以使用 Python [Qt 專案](https://www.qt.io/qt-for-application-development/)，又稱為 Python 的繫結[PySide （正式繫結）](http://wiki.qt.io/PySide) (另請參閱[PySide 下載](https://download.qt.io/official_releases/pyside/.)) 和[PyQt](https://wiki.python.org/moin/PyQt)。 目前，Visual Studio 中的 Python 支援不包含任何特定的 UI 開發工具。

## <a name="azure-sdk-for-python"></a>Azure SDK for Python
  
Azure SDK for Python 支援 Windows、Mac 和 Linux，可讓您更容易使用及管理 Microsoft Azure 服務。 詳細資料請參閱下列資源： 

- 若要安裝 SDK，請使用 [Python 封裝索引 (英文)](https://pypi.python.org/pypi/azure)，或遵循 Azure 文件中的[安裝 Python 和 SDK](https://azure.microsoft.com/documentation/articles/python-how-to-install/)。 
- [Azure SDK for Python 開發人員中心](https://azure.microsoft.com/develop/python/)中具有從安裝到具有教學課程之文件的大量說明。  一些重點如下：  
- 作法指南：
  - [儲存體 Blob](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [儲存體佇列](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [儲存體資料表](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [服務匯流排佇列](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [服務匯流排主題/訂用帳戶](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [服務管理](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

## <a name="scientific-computing"></a>科學運算

除了所有 Python 資料科學家程式庫，適用於 Visual Studio 的 Python 工具也支援 IPython 和 IPython Notebooks (可以在 Azure 中裝載)。

建議您從[加州大學爾灣分校 (英文)](http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack) 取得 IPython 和科學運算程式庫 (Matplotlib、Scipy、Numpy 等等)。  
  
## <a name="see-also"></a>另請參閱  

[Ptvs 快速入門：設定 Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
[ptvs 快速入門：開始撰寫程式碼 （專案）](../python/getting-started-with-ptvs-start-coding-projects.md)
[ptvs 快速入門：編輯程式碼](../python/getting-started-with-ptvs-editing-code.md)
[ptvs 快速入門：偵錯](../python/getting-started-with-ptvs-debugging.md)
[ptvs 快速入門：互動式 Python](../python/getting-started-with-ptvs-interactive-python.md)
[ptvs 快速入門：在 Azure 建置網站](../python/getting-started-with-ptvs-building-a-website-in-azure.md)
