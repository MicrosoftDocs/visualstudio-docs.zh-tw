---
title: Vspackage 中的資源 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 90674d17cdc3fb8956fd6eedeb3acb27226620cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696094"
---
# <a name="resources-in-vspackages"></a>VSPackage 中的資源
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

您可以在原生附屬 UI Dll、managed 附屬 Dll 或 managed VSPackage 本身中內嵌當地語系化的資源。  
  
 某些資源無法內嵌在 Vspackage 中。 您可以內嵌下列 managed 類型：  
  
- 字串  
  
- 封裝載入機碼 (也是字串)   
  
- 工具視窗圖示  
  
- 編譯的命令資料表輸出 (CTO) 檔  
  
- CTO 點陣圖  
  
- 命令列說明  
  
- 關於對話方塊資料  
  
  受管理套件中的資源是由資源識別碼所選取。 例外狀況是 CTO 檔案，必須命名為 CTMENU。 CTO 檔案必須以的形式出現在資源資料表中 `byte[]` 。 所有其他資源專案都是依類型來識別。  
  
  您可以使用 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 屬性來指出 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 該 managed 資源是否可用。  
  
  [!code-csharp[VSSDKResources#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdkresources/cs/vssdkresourcespackage.cs#1)]
  [!code-vb[VSSDKResources#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkresources/vb/vssdkresourcespackage.vb#1)]  
  
  <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>以這種方式設定，表示在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 搜尋資源（例如，使用）時，應該忽略未受管理的附屬 dll <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A> 。 如果 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 遇到兩個以上具有相同資源識別碼的資源，則會使用它所找到的第一個資源。  
  
## <a name="example"></a>範例  
 下列範例是工具視窗圖示的 managed 標記法。  
  
```  
<data name="1001"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyToolWinIcon.bmp;  
     System.Drawing.Bitmap,  
     System.Drawing,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
 下列範例示範如何內嵌必須命名為 CTMENU 的 CTO 位元組陣列。  
  
```  
<data name="CTMENU"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyPackage.cto;  
     System.Byte[],  
     mscorlib,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
## <a name="implementation-notes"></a>實作附註  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 盡可能延遲載入 Vspackage。 在 VSPackage 中內嵌 CTO 檔案的結果是，在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 安裝期間必須載入所有這類 vspackage，也就是在建立合併的命令資料表時。 藉由檢查中繼資料而不在 VSPackage 中執行程式碼，即可從 VSPackage 中解壓縮資源。 VSPackage 目前未初始化，因此效能損失最短。  
  
 在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 安裝之後從 VSPackage 要求資源時，該封裝可能已載入並初始化，因此效能損失最短。  
  
## <a name="see-also"></a>另請參閱  
 [受控 Vspackage](../../misc/managed-vspackages.md)   
 [管理 Vspackage](../../extensibility/managing-vspackages.md)   
 [MFC 應用程式中的當地語系化資源：附屬 Dll](https://msdn.microsoft.com/library/3a1100ae-a9c8-47b5-adbd-cbedef5992ef)   
 [Managed VSPackages](../../misc/managed-vspackages.md)
