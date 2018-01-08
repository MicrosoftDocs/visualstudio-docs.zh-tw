---
title: "簽署 VSIX 封裝 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ec875e6877b1c3ff1edf38b29c5e72b757021085
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="signing-vsix-packages"></a>簽署 VSIX 封裝
延伸模組組件不需要經過簽署才能在 Visual Studio 中，可以執行，但它是不錯的作法，若要這樣做。  
  
 如果您想要保護您的擴充功能，並確定沒有遭到竄改，您可以將數位簽章加入 VSIX 封裝。 當已簽署的 VSIX 時，VSIX 安裝程式會顯示訊息，指出它已簽署，再加上簽章本身的詳細資訊。 如果 VSIX 的內容已經遭到修改，而且尚未重新簽署此 VSIX，VSIX 安裝程式會顯示簽章無效。 安裝並不會停止，但會警告使用者。  
  
> [!IMPORTANT]
>  自 2015年起，使用 SHA256 加密以外的任何簽署 VSIX 封裝將會識別為具有簽章無效。 VSIX 安裝不會封鎖，但使用者將會收到警告。  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>簽章與 VSIXSignTool VSIX  
 沒有簽署工具可從 SHA256 加密[VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility)上在 nuget.org [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)。  
  
#### <a name="to-use-the-vsixsigntool"></a>若要使用 VSIXSignTool  
  
1.  將您的 VSIX，加入專案。  
  
2.  以滑鼠右鍵按一下專案節點，在 [方案總管] 中，選取**新增 &#124;管理 NuGet 封裝**。  如需 NuGet 並加入 NuGet 套件，請參閱詳細資訊，請參閱[NuGet 文件](/NuGet)和[封裝管理員 UI](/NuGet/Tools/Package-Manager-UI)主題。  
  
3.  搜尋從 VisualStudioExtensibility VSIXSignTool 並安裝 NuGet 套件。  
  
4.  您現在可以執行 VSIXSignTool 從專案的本機封裝位置。 為您簽署的案例，請參閱工具的命令列說明 (VSIXSignTool.exe /？)。  
  
 例如若要使用密碼登入受保護的憑證檔案：  
  
 VSIXSignTool.exe 登 /f\<憑證檔案 >/p\<密碼 > \<VSIXfile >  
  
## <a name="see-also"></a>請參閱  
 [推出 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)