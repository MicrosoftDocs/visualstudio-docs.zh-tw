---
title: 指定檔案名稱副檔名的檔案處理常式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aba754735bb8a002b1876770b47594ccc98e43fb
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56687532"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>指定適用於副檔名的檔案處理常式
有數種方式來判斷應用程式會處理具有特定副檔名的檔案。 OpenWithList 和 OpenWithProgids 動詞命令是兩種方式可以指定副檔名之登錄項目下的檔案處理常式。

## <a name="openwithlist-verb"></a>OpenWithList 動詞命令
 當您以滑鼠右鍵按一下檔案，以在 Windows 檔案總管中的時，您會看到**開啟**命令。 如果一個以上的產品與延伸模組相關聯，您會看到**開啟**子功能表。

 您可以註冊不同的應用程式可以藉由設定副檔名 OpenWithList 機碼 HKEY_CLASSES_ROOT 裡開啟延伸模組。 列出此檔案副檔名的機碼下的應用程式下方**建議程式**標題中**開啟** 對話方塊。 下列範例顯示開啟.vcproj 檔案的副檔名為您註冊應用程式。

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
>  指定的應用程式的索引鍵是 HKEY_CLASSES_ROOT\Applications 下方的清單。

 藉由新增 OpenWithList 金鑰，您會宣告您的應用程式支援檔案延伸模組，即使另一個應用程式會取得延伸模組的擁有權。 這可能是您的應用程式或其他應用程式的未來版本。

## <a name="openwithprogids"></a>OpenWithProgIDs
 以程式設計方式識別項 (Progid) 是易記版本 Classid 來識別應用程式或 COM 物件的版本。 每個共同建立的物件應該有它自己的 ProgID。 例如，VisualStudio.DTE.7.1 會啟動 Visual Studio.NET 2003 VisualStudio.DTE.10.0 啟動時[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 為專案類型或專案項目類型的擁有者，您必須建立檔案副檔名的版本特定 ProgID。 下列 Progid 可能是多餘的在於一個以上的 ProgID 可能會啟動相同的應用程式。 如需詳細資訊，請參閱 <<c0> [ 註冊的檔案名稱副檔名的動詞命令](../extensibility/registering-verbs-for-file-name-extensions.md)。

 使用版本控制檔案的 Progid 的下列命名慣例，以避免重複使用來自其他廠商的註冊：

|副檔名|版本控制 ProgID|
|--------------------|----------------------|
|.extension|產品名稱。 extension.versionMajor.versionMinor|

 您可以註冊不同的應用程式能夠開啟特定副檔名設定版本的 Progid 做為值加入 HKEY_CLASSES_ROOT\\*\<擴充功能 >* \OpenWithProgids 索引鍵。 此登錄機碼包含替代的 Progid 相關聯的檔案副檔名的清單。 列出的 Progid 相關聯的應用程式會出現在**開啟**_Product Name_子功能表。 如果相同的應用程式中同時指定`OpenWithList`和`OpenWithProgids`索引鍵，作業系統會將合併重複的項目。

> [!NOTE]
>  `OpenWithProgids`金鑰僅適用於 Windows XP 中。 因為其他作業系統會忽略此金鑰，請勿使用它作為唯一的註冊檔案處理常式。 若要提供更好的使用者體驗，在 Windows XP 中使用此金鑰。

 加入所需的 Progid 做為 REG_NONE 型別的值。 下列程式碼提供的 Progid 註冊副檔名的檔案範例 (。*ext*)。

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 指定為副檔名的預設值是預設的檔案處理常式的 ProgID。 如果您修改檔案延伸模組隨附於舊版的 ProgID[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]或，可以接手其他應用程式，則您必須註冊`OpenWithProgids`鍵檔案副檔名，並在清單中，連同指定的新 ProgID您支援舊的 Progid。 例如: 

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 如果舊 ProgID 有與其建立關聯的動詞命令，則這些動詞命令也會出現下**開啟** *Product Name*快顯功能表中。

## <a name="see-also"></a>另請參閱
- [關於副檔名](../extensibility/about-file-name-extensions.md)
- [註冊適用於副檔名的動詞命令](../extensibility/registering-verbs-for-file-name-extensions.md)