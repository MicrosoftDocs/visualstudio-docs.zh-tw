---
title: 指定檔案名副檔名的檔案處理常式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fbc85a506b51a29f1c4809890eaeeb0dcecc99a3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719572"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>指定適用於副檔名的檔案處理常式
有數種方式可以決定處理具有特定副檔名之檔案的應用程式。 OpenWithList 和 OpenWithProgids 動詞是兩種在副檔名的登錄專案底下指定檔案處理常式的方式。

## <a name="openwithlist-verb"></a>OpenWithList 動詞
 當您以滑鼠右鍵按一下 Windows Explorer 中的檔案時，會看到 [**開啟**] 命令。 如果有一個以上的產品與某個延伸模組相關聯，您會看到 [**開啟方式**] 子功能表。

 您可以藉由在 HKEY_CLASSES_ROOT 中設定副檔名的 OpenWithList 機碼，來註冊不同的應用程式來開啟擴充功能。 在 [**開啟方式**] 對話方塊中的 [**建議的程式**] 標題底下，會顯示 [檔案副檔名] 底下所列的應用程式。 下列範例顯示已註冊的應用程式，以開啟 vcproj 副檔名。

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> 指定應用程式的索引鍵來自 HKEY_CLASSES_ROOT\Applications. 底下的清單

 藉由新增 OpenWithList 鍵，您可以宣告應用程式是否支援副檔名，即使另一個應用程式取得延伸模組的擁有權也一樣。 這可能是您的應用程式或其他應用程式的未來版本。

## <a name="openwithprogids"></a>OpenWithProgIDs
 程式設計識別碼（Progid）是 Classid 的易記版本，可識別應用程式或 COM 物件的版本。 每個可共同產生的物件都應該有自己的 ProgID。 例如，VisualStudio 會在 VisualStudio 啟動時 Visual Studio .NET 2003 啟動 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 身為專案類型或專案專案類型的擁有者，您必須為您的副檔名建立版本特定的 ProgID。 這些 Progid 可能是多餘的，因為一個以上的 ProgID 可能會啟動相同的應用程式。 如需詳細資訊，請參閱[註冊副檔名的動詞](../extensibility/registering-verbs-for-file-name-extensions.md)。

 針對已設定版本的檔案 Progid，請使用下列命名慣例，以避免與其他廠商註冊的重複：

|副檔名|已建立版本的 ProgID|
|--------------------|----------------------|
|. 擴充功能|ProductName. versionMajor. versionMinor|

 您可以藉由將已建立版本的 Progid 當做值新增至 HKEY_CLASSES_ROOT\\ *\<延伸模組 >* \OpenWithProgids 索引鍵，來註冊可以開啟特定副檔名的不同應用程式。 此登錄機碼包含與副檔名相關聯的替代 Progid 清單。 與列出的 Progid 相關聯的應用程式會出現在 [**開啟方式**_產品名稱_] 子功能表中。 如果 `OpenWithList` 和 `OpenWithProgids` 機碼中同時指定了相同的應用程式，作業系統就會合並重複專案。

> [!NOTE]
> 只有在 Windows XP 中才支援 `OpenWithProgids` 金鑰。 由於其他作業系統會忽略此金鑰，因此請勿使用它做為檔案處理常式的唯一註冊。 使用此金鑰可在 Windows XP 中提供更好的使用者體驗。

 將想要的 Progid 新增為 REG_NONE 類型的值。 下列程式碼提供註冊副檔名（）之 Progid 的範例。*ext*）。

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 指定為副檔名預設值的 ProgID 是預設檔案處理常式。 如果您修改的 ProgID 適用于舊版 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 隨附的副檔名，或可由其他應用程式接管，則您必須註冊副檔名的 `OpenWithProgids` 金鑰，並在清單中指定新的 ProgID 以及舊的 ProgID您支援的。 例如:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 如果舊的 ProgID 具有相關聯的動詞，則這些動詞也會出現在快捷方式功能表中的 [**以***產品名稱*開啟] 底下。

## <a name="see-also"></a>請參閱
- [關於副檔名](../extensibility/about-file-name-extensions.md)
- [註冊適用於副檔名的動詞命令](../extensibility/registering-verbs-for-file-name-extensions.md)