---
title: 在 Vspackage 中的資源 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d252f61a9f634f4bb8435626c41c586bbe5cb839
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="resources-in-vspackages"></a>在 Vspackage 中的資源
您可以在 managed VSPackage 本身或原生附屬 UI Dll，受管理的附屬 Dll 中內嵌的當地語系化的資源。  
  
 在 Vspackage 中，不可以內嵌一些資源。 下列的 managed 型別可以內嵌：  
  
-   字串  
  
-   封裝載入機碼 （這也是字串）  
  
-   工具視窗圖示  
  
-   編譯的命令資料表輸出 (CTO) 檔案  
  
-   CTO 點陣圖  
  
-   命令列說明  
  
-   關於對話方塊資料  
  
 選取受管理的封裝中的資源的資源識別碼。 例外狀況是必須命名為 CTMENU 的 CTO 檔案。 CTO 檔案必須出現在做為資源表格`byte[]`。 所有其他資源項目會識別類型。  
  
 您可以使用<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>屬性來指出要[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]受管理的資源可供使用。  
  
 [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
 [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]  
  
 設定<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>以這種方式表示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]搜尋的資源，例如，使用時，應該忽略 unmanaged 的附屬 Dll <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>。 如果[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]遇到兩個或多個資源具有相同的資源識別碼，它會使用找到的第一個資源。  
  
## <a name="example"></a>範例  
 下列範例是受管理的工具視窗圖示表示。  
  
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
  
 下列範例示範如何內嵌必須命名為 CTMENU CTO 位元組陣列。  
  
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
  
## <a name="implementation-notes"></a>實作注意事項  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Vspackage，盡可能延遲載入。 結果的 CTO 檔案內嵌在 VSPackage 中，代表[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]必須在安裝期間，會建立合併的命令表時才會載入記憶體中的所有這類 Vspackage。 資源可以從中 VSPackage，藉由檢查不在 VSPackage 中執行程式碼的中繼資料。 VSPackage 未初始化在這個階段中，因此是最小的效能損失。  
  
 當[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage 在執行安裝程式中的資源要求，該封裝是可能已經載入和初始化，因此是最小的效能損失。  
  
## <a name="see-also"></a>另請參閱  
 [管理 Vspackage](../../extensibility/managing-vspackages.md)   
 [MFC 應用程式中的當地語系化資源：附屬 DLL](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)   
