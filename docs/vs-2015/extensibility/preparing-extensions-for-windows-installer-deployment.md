---
title: 準備 Windows Installer 部署擴充功能 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d4483fef9c200f6814c247f14ee956bfef4582e6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197921"
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>準備適用於 Windows Installer 部署的延伸模組
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您無法使用的 Windows Installer 套件 (MSI) 來部署的 VSIX 封裝。 不過，您可以擷取 MSI 部署的 VSIX 套件的內容。 本文件說明如何準備其預設輸出會包含在安裝專案中的 VSIX 套件的專案。  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>準備 Windows Installer 部署擴充功能專案  
 加入安裝專案之前，新的延伸模組專案上執行這些步驟。  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>若要準備擴充功能專案的 Windows Installer 部署  
  
1.  建立 VSPackage，MEF 元件、 編輯器 Adornment 或其他擴充性專案類型，其中包含 VSIX 資訊清單。  
  
2.  在程式碼編輯器中開啟 VSIX 資訊清單。  
  
3.  設定 VSIX 資訊清單的 InstalledByMsi 元素`true`。 如需 VSIX 資訊清單的詳細資訊，請參閱[VSIX 延伸結構描述 2.0 參考](../extensibility/vsix-extension-schema-2-0-reference.md)。  
  
     這可防止 VSIX 安裝程式在嘗試安裝的元件。  
  
4.  中的專案上按一下滑鼠右鍵**方案總管**然後按一下**屬性**。  
  
5.  選取 [ **VSIX** ] 索引標籤。  
  
6.  核取方塊標示**到下列位置複製 VSIX 內容**和輸入的路徑，安裝專案將會挑選檔案。  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>從現有的 VSIX 套件解壓縮檔案  
 執行下列步驟來將現有的 VSIX 套件的內容新增至安裝專案，當您沒有原始程式檔。  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>若要從現有的 VSIX 套件檔案解壓縮  
  
1.  重新命名。包含從延伸模組的 VSIX 檔案*檔名*.vsix 來*filename*.zip。  
  
2.  將.zip 檔案的內容複製到目錄。  
  
3.  從目錄中刪除 [Content_types].xml 檔案。  
  
4.  如先前程序中所示，請編輯 VSIX 資訊清單。  
  
5.  安裝程式專案中加入其餘的檔案。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio Installer 部署](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [逐步解說： 建立自訂動作](http://msdn.microsoft.com/en-us/4bd4b63a-2b91-431e-839c-5752443f0eaf)

