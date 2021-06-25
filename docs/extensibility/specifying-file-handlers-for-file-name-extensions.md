---
title: 指定副檔名的檔案處理常式 |Microsoft Docs
description: 瞭解如何使用 OpenWithList 和 OpenWithProgids，判斷哪一個應用程式處理 Visual Studio SDK 中的副檔名。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6ab370b4be8c12ad0df0c4822bcc7b487fb4aa21
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899442"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>指定適用於副檔名的檔案處理常式
有幾種方式可以決定處理具有特定副檔名之檔案的應用程式。 OpenWithList 和 OpenWithProgids 動詞是在副檔名的登錄專案底下指定檔案處理常式的兩種方式。

## <a name="openwithlist-verb"></a>OpenWithList 動詞
 當您以滑鼠右鍵按一下 Windows 檔案總管中的檔案時，您會看到 [ **開啟** ] 命令。 如果有一個以上的產品與某個擴充功能相關聯，您會看到 [ **開啟** ] 子功能表。

 您可以在 HKEY_CLASSES_ROOT 中設定副檔名的 OpenWithList 機碼，以註冊不同的應用程式來開啟擴充功能。 在 [**開啟** 檔案] 對話方塊中的 [**建議的程式**] 標題下，會出現列在此機碼底下的應用程式。 下列範例會顯示已註冊以開啟 vcproj 副檔名的應用程式。

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> 指定應用程式的索引鍵是來自 HKEY_CLASSES_ROOT\Applications 下的清單。

 藉由新增 OpenWithList 機碼，您可以宣告應用程式支援副檔名，即使另一個應用程式取得延伸模組的擁有權也一樣。 這可能是應用程式或其他應用程式的未來版本。

## <a name="openwithprogids"></a>OpenWithProgIDs
  (Progid) 的程式設計識別碼是識別應用程式或 COM 物件版本的易記 Classid 版本。 每個可共同使用的物件都應該有自己的 ProgID。 例如，VisualStudio 會在 VisualStudio 啟動時啟動 Visual Studio .NET [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 2003。 作為專案類型或專案專案類型的擁有者，您必須為您的副檔名建立版本特定的 ProgID。 這些 Progid 可能是多餘的，因為一個以上的 ProgID 可能會啟動相同的應用程式。 如需詳細資訊，請參閱 [註冊副檔名的動詞](../extensibility/registering-verbs-for-file-name-extensions.md)命令。

 針對已建立版本的檔案 Progid，請使用下列命名慣例，以避免與其他廠商的註冊重複：

|副檔名|已建立版本的 ProgID|
|--------------------|----------------------|
|. 副檔名|名稱. versionMajor. versionMinor|

 您可以藉由將已建立版本的 Progid 新增為 HKEY_CLASSES_ROOT \OpenWithProgids 索引鍵的值，來註冊可以開啟特定副檔名的不同應用程式 \\ *\<extension>* 。 此登錄機碼包含與副檔名相關聯的替代 Progid 清單。 與列出的 Progid 相關聯的應用程式會出現在 [ **開啟方式**_產品名稱_ ] 子功能表中。 如果同時在和機碼中指定相同的應用程式 `OpenWithList` `OpenWithProgids` ，則作業系統會合並重複專案。

> [!NOTE]
> `OpenWithProgids`只有在 WINDOWS XP 中才支援此金鑰。 因為其他作業系統會忽略此金鑰，所以請勿將它用作為檔案處理常式的唯一註冊。 您可以使用此金鑰在 Windows XP 中提供更好的使用者體驗。

 將所需的 Progid 新增為 REG_NONE 類型的值。 下列程式碼提供註冊 Progid 副檔名 ( 的範例。*ext*) 。

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 指定為副檔名預設值的 ProgID 是預設的檔案處理常式。 如果您針對舊版隨附 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 或可由其他應用程式取得的副檔名修改 ProgID，則必須 `OpenWithProgids` 為您的副檔名註冊金鑰，並在清單中指定新的 progid 以及您支援的舊 progid。 例如：

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 如果舊的 ProgID 有相關聯的動詞，則這些動詞命令也會出現在快捷方式功能表中的 [開啟檔案] **和**[ *產品名稱* ] 底下。

## <a name="see-also"></a>另請參閱
- [關於副檔名](../extensibility/about-file-name-extensions.md)
- [註冊適用於副檔名的動詞命令](../extensibility/registering-verbs-for-file-name-extensions.md)
