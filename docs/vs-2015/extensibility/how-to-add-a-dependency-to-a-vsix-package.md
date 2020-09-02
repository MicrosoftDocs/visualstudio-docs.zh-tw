---
title: 如何：將相依性新增至 VSIX 套件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 997c0df133b72d69dfb4e69de53a1b77e1a0965c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697499"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>如何︰將相依性加入至 VSIX 封裝
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以設定 VSIX 封裝部署，以安裝任何尚未存在於目的電腦上的相依性。 若要完成這項工作，請將 VSIX 相依性加入 extension.vsixmanifest 檔案。  
  
#### <a name="to-add-a-dependency"></a>新增相依性  
  
1. 在 **設計** 視圖中開啟 extension.vsixmanifest 檔案。 移 **至 [相依** 性] 索引標籤，然後按一下 [ **新增**]。  
  
2. 若要加入已安裝的擴充功能：在 [ **加入新** 的相依性] 對話方塊中，選取 [ **已安裝的延伸** 模組]，然後在 [ **名稱**] 中選取清單上的延伸模組。  
  
3. 若要加入另一個未安裝的 VSIX：：在 [ **加入新** 的相依性] 對話方塊中，選取 [檔 **系統上** 的檔案]，然後使用 [ **流覽]** 按鈕來選取 VSIX。  
  
## <a name="see-also"></a>另請參閱  
 [VSIX 延伸架構1.0 參考](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [VSIX 封裝的剖析](../extensibility/anatomy-of-a-vsix-package.md)   
 [準備適用於 Windows Installer 部署的延伸模組](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
