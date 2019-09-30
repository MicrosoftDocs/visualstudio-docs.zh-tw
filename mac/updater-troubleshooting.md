---
title: 更新程式在擷取資訊時發生錯誤
description: 當您看到錯誤 [擷取更新資訊時發生錯誤] 時，該如何修正的指示。 在 Visual Studio 2019 for Mac 中
ms.topic: troubleshooting
author: asb3993
ms.author: amburns
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: 5ba295defe19c6f3c6c56d5bccc7cc3fa367bb50
ms.sourcegitcommit: cf8c0fef2b9690595e99ce3802586cdd55fd37c2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107775"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>疑難排解：更新程式在擷取資訊時發生錯誤

在極少數情況下，當您嘗試[更新 Visual Studio for Mac](update.md) 時，您可能會看到顯示錯誤訊息 [擷取更新資訊時發生錯誤]。 如果發生此錯誤，請嘗試下列步驟來修正：

- 檢查網際網路連線。 連線中斷是造成此錯誤最常見的原因。
  - 如果下載元件失敗，您可以按一下元件名稱旁邊的重試按鈕，以嘗試再次下載。
- 重新啟動 IDE。
- 如果您繼續看到此錯誤訊息，若 **.dmg** 仍在您的機器上 (或者您可以從 [visualstudio.com](https://visualstudio.microsoft.com/vs/mac/) 下載)，您也可以嘗試使用安裝程式來更新
  - 安裝程式會更新您機器上任何已安裝的元件。
  - 藉由重新執行安裝程式，您也可以安裝先前未安裝的任何遺漏元件。
- 您也可以藉由刪除位在 `~/Library/Caches/VisualStudio/7.0/TempDownload/index.xml` 的檔案，以嘗試清除快取檔案。
