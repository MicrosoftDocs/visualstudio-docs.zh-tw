---
title: 簽署 VSIX 封裝 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ba9d5ac7d9700d8ff5b047134a53d0147af3a78f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827189"
---
# <a name="signing-vsix-packages"></a>簽署 VSIX 套件
延伸模組組件不需要經過簽署才能在 Visual Studio 中，可以執行，但最好這麼做。  
  
 如果您想要保護您的延伸模組，並確定未遭到竄改，您可以加入 VSIX 封裝來數位簽章。 當已簽署 VSIX 時，VSIX 安裝程式會顯示一則訊息指出它已簽署，再加上簽章本身的相關詳細資訊。 如果有已修改的 VSIX 內容，尚未重新簽署 VSIX，VSIX 安裝程式將會顯示簽章無效。 安裝並不會停止，但會警告使用者。  
  
> [!IMPORTANT]
>  從 Visual Studio 2015 開始，使用 SHA256 加密以外的任何簽署 VSIX 封裝將會識別為具有無效簽章。 VSIX 安裝未遭到封鎖，但使用者將會收到警告。  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>簽署與 VSIXSignTool VSIX  
 沒有簽署工具可從 SHA256 加密[VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility)在 nuget.org 上[VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)。  
  
#### <a name="to-use-the-vsixsigntool"></a>若要使用 VSIXSignTool  
  
1. 將您的 VSIX，加入專案。  
  
2. 以滑鼠右鍵按一下專案節點，在 [方案總管] 中，選取**新增&#124;管理 NuGet 套件**。  如需詳細資訊，NuGet 和加入 NuGet 套件請參閱[NuGet 文件](/NuGet)並[套件管理員 UI](/NuGet/Tools/Package-Manager-UI)主題。  
  
3. 搜尋從 VisualStudioExtensibility VSIXSignTool 並安裝 NuGet 套件。  
  
4. 您現在可以執行 VSIXSignTool 從專案的本機封裝的位置。 如您簽署的案例，請參閱工具的命令列說明 (VSIXSignTool.exe /？)。  
  
   例如若要使用密碼保護的憑證檔簽署的資訊：  
  
   VSIXSignTool.exe 登 /f \<certfile >/p\<密碼 > \<VSIXfile >  
  
## <a name="see-also"></a>另請參閱  
 [推出 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)
