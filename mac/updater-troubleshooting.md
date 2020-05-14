---
title: 更新程式在擷取資訊時發生錯誤
description: 當您看到錯誤 [擷取更新資訊時發生錯誤] 時，該如何修正的指示。 在 Visual Studio 2019 for Mac 中
ms.topic: troubleshooting
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: 2ccef07a2889f66df3e7f217ea292b61ffc0008f
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "75405468"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>故障排除：更新程式檢索資訊時出錯

在極少數情況下，當您嘗試[更新 Visual Studio for Mac](update.md) 時，您可能會看到顯示錯誤訊息 [擷取更新資訊時發生錯誤]。 如果發生此錯誤，請嘗試下列步驟來修正：

- 請檢查網際網路連線。 連線中斷是造成此錯誤最常見的原因。
  - 如果下載元件失敗，您可以按一下元件名稱旁邊的重試按鈕，以嘗試再次下載。
- 重新啟動 IDE。
- 如果您繼續看到此錯誤訊息，若 **.dmg** 仍在您的機器上 (或者您可以從 [visualstudio.com](https://visualstudio.microsoft.com/vs/mac/) 下載)，您也可以嘗試使用安裝程式來更新
  - 安裝程式會更新您機器上任何已安裝的元件。
  - 藉由重新執行安裝程式，您也可以安裝先前未安裝的任何遺漏元件。
- 您也可以藉由刪除位在 `~/Library/Caches/VisualStudio/8.0/TempDownload/index.xml` 的檔案，以嘗試清除快取檔案。
- 如果您正在使用適用于 Mac 的舊版本的 Visual Studio，則`VisualStudio`目錄下可能還有其他版本號。 刪除`index.xml`這些路徑中的檔。
