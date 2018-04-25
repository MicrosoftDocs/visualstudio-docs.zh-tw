---
title: 指定副檔名的檔案處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0d0086f8badb32431c85f16e1f74fe8f186c9b2e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>指定副檔名的檔案處理常式
有數種方式可判斷應用程式會處理具有特定副檔名的檔案。 OpenWithList 和 OpenWithProgids 動詞命令是兩種方式指定之副檔名的登錄項目下的檔案處理常式。  
  
## <a name="openwithlist-verb"></a>OpenWithList 動詞命令  
 當您以滑鼠右鍵按一下檔案，以在 Windows 檔案總管 中的時，您會看到**開啟**命令。 如果多個產品都與擴充功能，您會看到**開啟**子功能表。  
  
 您可以註冊不同的應用程式開啟 HKEY_CLASSES_ROOT 中設定之副檔名的 OpenWithList 索引鍵的延伸模組。 此機碼的檔案副檔名底下列出的應用程式出現在**建議程式**標題中**開啟** 對話方塊。 下列範例會顯示無法開啟.vcproj 檔案延伸模組已註冊的應用程式。  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
>  指定的應用程式的索引鍵是 HKEY_CLASSES_ROOT\Applications 下方的清單。  
  
 藉由加入非 OpenWithList 金鑰，您會宣告您的應用程式支援檔案延伸模組，即使另一個應用程式會取得延伸模組的擁有權。 這可能是您的應用程式或其他應用程式的未來版本。  
  
## <a name="openwithprogids"></a>OpenWithProgIDs  
 以程式設計方式識別項 (Progid) 是識別應用程式或 COM 物件的版本中的 Classid 易記版本。 每個共同建立的物件應該有它自己的 ProgID。 例如，VisualStudio.DTE.7.1 會啟動 Visual Studio.NET 2003 VisualStudio.DTE.10.0 啟動時[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 專案類型或專案項目類型的擁有者，您必須建立版本特定 ProgID 檔案副檔名。 下列 Progid 可能是多餘的在於一個以上的 ProgID 可能啟動相同的應用程式。 如需詳細資訊，請參閱[註冊副檔名的動詞命令](../extensibility/registering-verbs-for-file-name-extensions.md)。  
  
 使用下列命名慣例版本化檔案的 Progid，以避免重複使用其他廠商的註冊：  
  
|副檔名|已建立版本 ProgID|  
|--------------------|----------------------|  
|.extension|產品名稱。 extension.versionMajor.versionMinor|  
  
 您可以註冊不同的應用程式能夠開啟特定的副檔名，將建立版本的 Progid 做為值加入至 HKEY_CLASSES_ROOT\\*\<副檔名 >* \OpenWithProgids 索引鍵。 此登錄機碼包含替代的 Progid 相關聯的副檔名的清單。 列出的 Progid 相關聯的應用程式出現在 **開啟 * * * 產品名稱*子功能表。 如果相同的應用程式中同時指定`OpenWithList`和`OpenWithProgids`索引鍵，作業系統會合併重複的項目。  
  
> [!NOTE]
>  `OpenWithProgids`金鑰僅適用於在 Windows XP。 因為其他作業系統會忽略這個索引鍵，請勿使用它做為唯一的註冊檔案處理常式。 使用此金鑰，以提供在 Windows XP 中的較佳使用者體驗。  
  
 加入所需的 Progid 做為 REG_NONE 類型的值。 下列程式碼會提供的 Progid 註冊的檔案副檔名 (。*ext*)。  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 指定為副檔名的預設值是預設檔案處理常式的 ProgID。 如果您修改隨附於舊版的檔案副檔名 ProgID[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]或，可以接手其他應用程式，則您必須註冊`OpenWithProgids`檔案副檔名索引鍵，並連同 清單中指定的新 ProgID舊的 Progid，您的支援。 例如:   
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 如果舊 ProgID 具有與它相關聯的動詞命令，則這些動詞命令也會出現在**開啟***產品名稱*快顯功能表中。  
  
## <a name="see-also"></a>另請參閱  
 [關於檔案名稱副檔名](../extensibility/about-file-name-extensions.md)   
 [註冊適用於副檔名的動詞命令](../extensibility/registering-verbs-for-file-name-extensions.md)