---
title: "如何： 加入 VSIX 封裝的相依性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d3f3b54e19d8418f35a733b73ea0616b53bd42ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>如何： 將相依性加入至 VSIX 封裝
您可以設定安裝中不存在目標電腦上任何相依性的 VSIX 封裝部署。 若要完成此動作，包含 VSIX 相依性，source.extension.vsixmanifest 檔案。  
  
#### <a name="to-add-a-dependency"></a>若要加入相依性  
  
1.  中，開啟 source.extension.vsixmanifest 檔案**設計**檢視。 移至**相依性**索引標籤上，按一下 **新增**。  
  
2.  若要加入已安裝的擴充： 中**加入新的相依性**對話方塊中，選取**安裝擴充功能**，然後針對**名稱**，選取清單上的擴充功能。  
  
3.  若要加入另一個未安裝的 VSIX:: 中**加入新的相依性**對話方塊中，選取**檔案系統上**，然後使用**瀏覽** 按鈕以選取 VSIX。  
  
## <a name="see-also"></a>另請參閱  
 [VSIX 擴充功能的結構描述 1.0 參考](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [VSIX 封裝的結構](../extensibility/anatomy-of-a-vsix-package.md)   
 [準備適用於 Windows Installer 部署的擴充功能](../extensibility/preparing-extensions-for-windows-installer-deployment.md)