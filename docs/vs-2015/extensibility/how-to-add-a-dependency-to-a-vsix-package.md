---
title: 如何： 新增 vsix 套見的相依性 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ebd835fef9df8fbdeb67bdf9c7e6eff31bcf4730
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497330"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>如何： 將相依性加入至 VSIX 封裝
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 將相依性加入至 VSIX 封裝](https://docs.microsoft.com/visualstudio/extensibility/how-to-add-a-dependency-to-a-vsix-package)。  
  
您可以設定安裝中不存在目標電腦上任何相依性的 VSIX 套件部署。 若要這麼做，包括 source.extension.vsixmanifest 檔案 VSIX 相依性。  
  
#### <a name="to-add-a-dependency"></a>新增相依性  
  
1.  開啟 source.extension.vsixmanifest 檔案中的**設計**檢視。 移至**相依性**索引標籤，然後按一下**新增**。  
  
2.  若要新增已安裝延伸模組： 在**加入新的相依性**對話方塊中，選取**已安裝擴充功能**，然後針對**名稱**，選取清單上的擴充功能。  
  
3.  若要新增另一個未安裝的 VSIX:: 中**加入新的相依性**對話方塊中，選取**在檔案系統上的檔案**，然後使用**瀏覽**按鈕來選取 VSIX。  
  
## <a name="see-also"></a>另請參閱  
 [VSIX 延伸結構描述 1.0 參考](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [VSIX 封裝的結構](../extensibility/anatomy-of-a-vsix-package.md)   
 [準備適用於 Windows Installer 部署的擴充功能](../extensibility/preparing-extensions-for-windows-installer-deployment.md)

