---
title: 使用延伸模組組件項目範本建立的延伸模組組件 |Microsoft Docs
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: chitray
ms.author: chitray
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: 55ceb788807f5d4fc9de2a96b4d359f290218dda
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866318"
---
# <a name="walkthrough-create-an-extension-pack"></a>逐步解說：建立延伸模組套件

延伸模組組件是一組可一起安裝的延伸模組。 延伸模組組件可讓您輕鬆地與其他使用者共用您最愛的擴充功能或套件組合的一組一起應付特定案例的擴充功能。
  
## <a name="prerequisites"></a>必要條件

從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  

延伸模組套件功能可從 Visual Studio 15.8 Preview 2 開始。
  
## <a name="create-an-extension-with-an-extension-pack-item-template"></a>使用延伸模組組件項目範本建立擴充功能

延伸模組組件項目範本建立與一組可一起安裝的擴充功能的延伸模組組件。
  
1. 在 **新的專案**對話方塊方塊中，展開**Visual C#** 或**Visual Basic** ，然後按一下 **擴充性**。 在 **範本**窗格中，選取**VSIX 專案**。 在 [名稱]  方塊中，輸入 `Test Extension Pack`。 按一下 [確定 **Deploying Office Solutions**]。  
  
2. 在 **方案總管**，以滑鼠右鍵按一下專案節點，然後選取**新增 / 新項目**。 移至 Visual C#**擴充性**節點，然後選取**延伸模組套件**。 保留預設的檔案名稱 (ExtensionPack1.cs)。  
  
3. ExtensionPack1.vsext 檔案會加入包含下列程式碼

   ```json
   {
    "id": "ExtensionPack1",
    "name": "ExtensionPack1",
    "description": "Read about creating extension packs at https://aka.ms/vsextpack",
    "version": "1.0.0.0",
    "extensions": [  // List of extensions that are included in the Extension Pack.
      {
        "vsixId": "41858b2d-ff0b-4a43-80b0-f1b2d6084935", // The vsix id of the extension you want to   include.
        "name": "AlignAssignments"
      },
      {
          "vsixId": "42374550-426a-400e-96f9-237682e8dea6",
        "name": "CopyAsHtml"
      }
    ]
   }  
   ```

4. 要包含在延伸模組套件中的延伸模組的 vsixid 都位於[Visual Studio Marketplace](https://marketplace.visualstudio.com/)。 尋找您想要加入，然後按一下 擴充的功能**複製識別碼**。 您可以更新現有**vsixId**在上述檔案或另一個延伸模組新增至清單。

    ![從 Marketplace 複製 VsixId](media/vsixid-marketplace.png)

5. 建置專案，並將您的延伸模組上傳至 Marketplace。 請參閱[發行的 Visual Studio 擴充功能](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)。 
    
> [!NOTE]
> 延伸模組套件只能安裝可用的延伸模組[Visual Studio Marketplace](https://marketplace.visualstudio.com/)或是[私用組件庫](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)。
 
## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>從 Visual Studio Marketplace 安裝延伸模組套件

現在，發佈擴充功能時，將它安裝在 Visual Studio，並測試其存在。

1. 在 Visual Studio 中，在**工具**功能表上，按一下 **擴充功能和更新...**.

2. 按一下 **線上**，然後搜尋`Test Extension Pack`。

3. 按一下 [ **下載**]。 擴充功能和擴充功能套件中包含的延伸模組的清單則會排程進行安裝。

4. 以下是範例延伸模組套件，下載檢視**擴充功能和更新**對話方塊。 如果您想要只是一些包含擴充功能安裝延伸模組組件中，您可以修改的延伸模組清單中**排定安裝**。

    ![從 Marketplace 下載延伸模組組件](media/vside-extensionpack.png)

5. 若要完成安裝，請關閉 Visual Studio 的所有執行個體。

## <a name="remove-the-extension"></a>移除擴充功能

若要從您的電腦中移除擴充功能：

1. 在 Visual Studio 中，在**工具**功能表上，按一下 **延伸模組和更新...**.

2. 選取  `Test Extension Pack` ，然後按一下 **解除安裝**。 擴充功能和擴充功能套件中包含的延伸模組清單然後會排程進行解除安裝。

3. 若要完成解除安裝，請關閉所有 Visual Studio 執行個體。
