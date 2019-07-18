---
title: 作法：手動封裝擴充功能 （VSIX 部署） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: d25990e0-e782-4a79-9d9a-1caf3c56c6a2
caps.latest.revision: 10
manager: jillfra
ms.openlocfilehash: e4d721fca8d429fe81de30306a8823e3d7fd9cab
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65681685"
---
# <a name="how-to-manually-package-an-extension-vsix-deployment"></a>HOW TO：手動封裝擴充功能 （VSIX 部署）
您可以建立 VSIX 封裝，來包裝進行部署的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 擴充功能。 建立封裝的方法有三種：  
  
- 使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] SDK 隨附的其中一個擴充性範本，來建立 VSIX 封裝專案。 這對大多數的情況下是最簡單的選項。  
  
- 將擴充功能專案的輸出包裝在空白 [VSIX 專案](../extensibility/vsix-project-template.md)中。 建議將這個選項用於範本、不支援的組件和自訂類型。  
  
- 手動建立 VSIX 封裝。 只有在另兩個選項都無法使用時，才建議使用這個選項。  
  
  本文件描述第三個選項。  
  
## <a name="creating-a-vsix-package"></a>建立 VSIX 封裝  
 若要手動封裝擴充功能，請將 extension.manifest 檔案和 [Content_Types].xml 檔案加入擴充功能專案中，並將它們與組建輸出一起放在壓縮檔中，並重新命名壓縮檔，使其具有 .vsix 副檔名。 要封裝的擴充功能必須是 [VSIX 結構描述](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)所支援的類型。  
  
> [!NOTE]
> VSIX 封裝中的檔案名稱不得包含空格，也不下定義的保留在統一資源識別元 (URI)，做為字元[ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339)。  
  
#### <a name="to-manually-create-a-vsix-package"></a>手動建立 VSIX 封裝  
  
1. 建立 VSIX 結構描述所支援類型的 Visual Studio 擴充功能。  
  
2. 建立 XML 檔案，並將它命名為 `extension.vsixmanifest`。  
  
3. 根據 VSIX 結構描述，來填寫 extension.vsixmanifest 檔案。 如需範例資訊清單，請參閱 [PackageManifest 項目 (根項目、VSX 結構描述)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187)。  
  
4. 建立第二個 XML 檔案，並將它命名為 `[Content_Types].xml`。  
  
5. 填寫 [Content_Types].xml 檔案中所指定[結構 Content_types\].xml 檔案](../extensibility/the-structure-of-the-content-types-dot-xml-file.md)。  
  
6. 將這兩個 XML 檔案與要部署的擴充功能一起放在目錄中。  
  
     如果是專案範本或項目範本，請將包含範本的 .zip 檔案放在與 XML 檔案相同的資料夾中。 請不要將 XML 檔案放在 .zip 檔案中。  
  
     在所有其他情況下，將 XML 檔案放在與組建輸出相同的目錄中。  
  
7. 在 Windows 檔案總管中，以滑鼠右鍵按一下包含擴充功能內容的資料夾和兩個 XML 檔案，並按一下 [傳送到] ，然後按一下 [壓縮的 (zipped) 資料夾] 。  
  
8. 將產生的 .zip 檔案重新命名為 *檔案名稱*.vsix，其中 *檔案名稱* 是安裝封裝的可轉散發檔案名稱。  
  
## <a name="see-also"></a>另請參閱  
 [推出 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)   
 [VSIX 封裝的結構](../extensibility/anatomy-of-a-vsix-package.md)   
 [PackageManifest 項目 （根項目、 VSX 結構描述）](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187)