---
title: "準備 Windows Installer 部署的擴充功能 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6d9568cd6fd26683e035ed9889e0d0b7928ce799
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>準備 Windows Installer 部署的擴充功能
若要部署的 VSIX 封裝，您無法使用 Windows Installer 封裝 (MSI)。 不過，您可以將 MSI 部署的 VSIX 套件的內容解壓縮。 本文件說明如何準備的預設輸出，則為 VSIX 封裝，以包含在安裝專案的專案。  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>準備 Windows Installer 部署的擴充功能專案  
 在新的延伸模組專案上執行這些步驟，然後再新增至安裝專案。  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>準備 Windows Installer 部署擴充功能專案  
  
1.  建立 VSPackage，MEF 元件、 編輯器裝飾或包含 VSIX 資訊清單的其他擴充性專案類型。  
  
2.  程式碼編輯器中開啟的 VSIX 資訊清單。  
  
3.  設定 VSIX 資訊清單的 InstalledByMsi 元素`true`。 如需 VSIX 資訊清單的詳細資訊，請參閱[VSIX 延伸結構描述 2.0 參照](../extensibility/vsix-extension-schema-2-0-reference.md)。  
  
     這可防止 VSIX 安裝程式嘗試安裝的元件。  
  
4.  中的專案上按一下滑鼠右鍵**方案總管 中**按一下**屬性**。  
  
5.  選取**VSIX**  索引標籤。  
  
6.  核取方塊標示為**到下列位置複製 VSIX 內容**輸入其中安裝專案將會收取檔案的路徑。  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>從現有的 VSIX 套件解壓縮檔案  
 執行下列步驟來將現有的 VSIX 套件的內容加入至安裝專案，當您不需要原始程式檔。  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>若要從現有的 VSIX 套件解壓縮檔案  
  
1.  重新命名。包含來自的延伸模組的 VSIX 檔案*filename*至.vsix *filename*.zip。  
  
2.  將.zip 檔案的內容複製到目錄。  
  
3.  從目錄刪除 [Content_types].xml 檔案。  
  
4.  編輯 VSIX 資訊清單，如先前程序中所示。  
  
5.  將其餘的檔案加入至安裝專案。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 安裝程式部署](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [逐步解說： 建立自訂動作](http://msdn.microsoft.com/en-us/4bd4b63a-2b91-431e-839c-5752443f0eaf)