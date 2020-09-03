---
title: 簽署 VSIX 套件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4efaaa78ce593d8b97d1df454a9c30c2e62d9f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918730"
---
# <a name="signing-vsix-packages"></a>簽署 VSIX 套件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

擴充功能元件不需要經過簽署，就可以在 Visual Studio 中執行，但這是很好的作法。  
  
 如果您想要保護您的延伸模組，並確定其未遭篡改，您可以將數位簽章新增至 VSIX 套件。 當 VSIX 經過簽署時，VSIX 安裝程式會顯示訊息，指出它已簽署，以及簽章本身的詳細資訊。 如果 VSIX 的內容已經過修改，而且 VSIX 尚未重新簽署，則 VSIX 安裝程式會顯示簽章無效。 安裝未停止，但使用者會收到警告。  
  
> [!IMPORTANT]
> 從2015開始，以 SHA256 加密以外的任何方式簽署的 VSIX 套件將會識別為具有無效簽章。 未封鎖 VSIX 安裝，但使用者將會收到警告。  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>使用 VSIXSignTool 簽署 VSIX  
 Nuget.org 上的 [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) 提供了 SHA256 加密簽署工具，網址為 [VsixSignTool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)。  
  
#### <a name="to-use-the-vsixsigntool"></a>若要使用 VSIXSignTool  
  
1. 將您的 VSIX 新增至專案。  
  
2. 以滑鼠右鍵按一下方案總管中的專案節點，然後選取 [ **新增 &#124; 管理 NuGet 封裝**]。  如需 NuGet 和新增 NuGet 套件的詳細資訊，請參閱 [Nuget 總覽](/nuget/) 和 [使用對話方塊管理 nuget 套件](/nuget/consume-packages/install-use-packages-visual-studio)。  
  
3. 從 VisualStudioExtensibility 搜尋 VSIXSignTool 並安裝 NuGet 套件。  
  
4. 您現在可以從專案的本機套件位置執行 VSIXSignTool。 請參閱工具的命令列說明，以瞭解簽署案例 ( # A0/？ ) 。  
  
   例如，使用受密碼保護的憑證檔案來簽署：  
  
   VSIXSignTool.exe sign/f \<certfile> /p \<password>\<VSIXfile>  
  
## <a name="see-also"></a>另請參閱  
 [推出 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)
