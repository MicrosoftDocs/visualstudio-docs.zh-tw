---
title: VSIX 專案範本 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bff05b0b1b05a6b00b7924f0fb5bfc957adba41c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="vsix-project-template"></a>VSIX 專案範本
您可以使用 VSIX 專案範本來將一或多個 Visual Studio 擴充功能包裝在 VSIX 專案，並再將封裝發佈上[Visual Studio 組件庫](http://go.microsoft.com/fwlink/?LinkID=123847)網站。  
  
 VSIX 部署支援 Vspackage、 組件、 MEF 元件、 專案範本、 項目範本，[工具箱] 控制項和自訂延伸模組類型。  
  
> [!NOTE]
>  若要使用 VSIX 專案，您必須安裝 Visual Studio SDK。 如需有關 Visual Studio SDK 的詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="where-to-find-the-vsix-project-template"></a>如何尋找 VSIX 專案範本  
 VSIX 專案範本會用於**新專案** 對話方塊。 展開  **Visual Basic**節點或**Visual C#**  節點，然後選擇 **擴充性**。  
  
> [!TIP]
>  您應該確定該.NET Framework 4.5 或更新版本中頂端的下拉式清單中指定**新專案** 對話方塊。  
  
## <a name="uses-of-the-vsix-project-template"></a>VSIX 專案範本的用法  
 VSIX 專案範本有兩個主要用途：  
  
-   若要部署專案範本、 項目範本和尚無 VSIX 支援其他擴充功能。  
  
-   若要將多個延伸模組的輸出包裝成一種部署套件。  
  
 您沒有使用 VSIX 專案範本來部署 Vspackage 或其他類型的已支援 VSIX 擴充功能。  
  
## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>封裝中的空白 VSIX 專案的延伸模組  
 您可以將現有的延伸模組或未安裝支援，其包裝在空白的 VSIX 專案的 VSIX 擴充功能封裝。 要包裝的擴充功能必須是支援的型別[VSIX 結構描述](../extensibility/vsix-extension-schema-2-0-reference.md)。  
  
#### <a name="to-package-an-extension-by-using-a-vsix-project"></a>若要使用 VSIX 專案封裝擴充功能  
  
1.  建置專案，您的延伸模組所組成。  
  
2.  使用建立 VSIX 專案**VSIX 專案**範本。  
  
     在中，開啟 Source.extension.vsixmanifest**資訊清單設計工具**。  
  
3.  在**資產**索引標籤上，選擇**新增** 按鈕。  
  
     **加入新資產** 對話方塊隨即出現。  
  
4.  在**類型**清單中，選擇要加入之擴充的類型。  
  
5.  若要加入的擴充功能或內容的項目，包含在目前方案中 （例如，項目範本或編譯的組件），請執行下列步驟：  
  
    1.  在**來源**清單中，選擇**目前方案中的專案**。  
  
    2.  在**專案**清單中，選擇 擴充功能的名稱。  
  
    3.  在**此資料夾中的內嵌**方塊中，輸入用來內嵌資產，，然後選擇 [資料夾名稱**確定**] 按鈕。  
  
6.  若要加入擴充功能或不包含在目前方案的內容項目，執行下列步驟：  
  
    1.  在**來源**清單方塊中，選擇**檔案系統上的檔案**。  
  
    2.  在**路徑**欄位中輸入完整路徑或壓縮編譯延伸模組檔案，或者使用**瀏覽**按鈕瀏覽至檔案。  
  
    3.  在**此資料夾中的內嵌**方塊中，輸入用來內嵌資產，，然後選擇 [資料夾名稱**確定**] 按鈕。  
  
7.  如果您要封裝包括其他擴充功能，請將其加入相同的方式。  
  
8.  建置方案。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 建置包含 VSIX 資訊清單檔案、 [Content_Types].xml 檔案，以及所有您加入至專案的延伸模組資產.vsix 檔案。  
  
## <a name="see-also"></a>另請參閱  
 [VSIX 擴充功能 2.0 結構描述參考](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [尋找和使用 Visual Studio 延伸模組](../ide/finding-and-using-visual-studio-extensions.md)