---
title: 準備 Windows Installer 部署擴充功能 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ef69ac45a090aa4395aa15d1395cff1665255b51
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639109"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>準備 Windows Installer 部署擴充功能
您無法使用的 Windows Installer 套件 (MSI) 來部署的 VSIX 封裝。 不過，您可以擷取 MSI 部署的 VSIX 套件的內容。 本文件說明如何準備其預設輸出會包含在安裝專案中的 VSIX 套件的專案。  
  
## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>準備 Windows Installer 部署擴充功能專案  
 加入安裝專案之前，新的延伸模組專案上執行這些步驟。  
  
### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>若要準備擴充功能專案的 Windows Installer 部署  
  
1.  建立 VSPackage，MEF 元件、 編輯器 Adornment 或其他擴充性專案類型，其中包含 VSIX 資訊清單。  
  
2.  在程式碼編輯器中開啟 VSIX 資訊清單。  
  
3.  設定`InstalledByMsi`VSIX 資訊清單的項目`true`。 如需 VSIX 資訊清單的詳細資訊，請參閱[VSIX 延伸結構描述 2.0 參考](../extensibility/vsix-extension-schema-2-0-reference.md)。  
  
     這可防止 VSIX 安裝程式在嘗試安裝的元件。  
  
4.  中的專案上按一下滑鼠右鍵**方案總管**然後按一下**屬性**。  
  
5.  選取 [ **VSIX** ] 索引標籤。  
  
6.  核取方塊標示**到下列位置複製 VSIX 內容**和輸入的路徑，安裝專案將會挑選檔案。  
  
## <a name="extract-files-from-an-existing-vsix-package"></a>從現有的 VSIX 套件檔案解壓縮  
 執行下列步驟來將現有的 VSIX 套件的內容新增至安裝專案，當您沒有原始程式檔。  
  
### <a name="to-extract-files-from-an-existing-vsix-package"></a>若要從現有的 VSIX 套件檔案解壓縮  
  
1.  重新命名 *。VSIX*檔案，其中包含從延伸模組*filename.vsix*要*filename.zip*。  
  
2.  複製的內容 *.zip*到目錄的檔案。  
  
3.  刪除 *[Content_types].xml*從目錄的檔案。  
  
4.  如先前程序中所示，請編輯 VSIX 資訊清單。  
  
5.  安裝程式專案中加入其餘的檔案。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio installer 部署](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [逐步解說： 建立自訂動作](http://msdn.microsoft.com/en-us/4bd4b63a-2b91-431e-839c-5752443f0eaf)