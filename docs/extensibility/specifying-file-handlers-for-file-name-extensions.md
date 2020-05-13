---
title: 為檔案名副檔名指定檔案處理程式 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af195aea09c91696843c6be42c20053bb8c095a2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699759"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>指定適用於副檔名的檔案處理常式
有許多方法可以確定處理具有特定文件副檔名的檔案的應用程式。 OpenWithList 和 OpenWithProgids 謂詞是兩種在檔擴展名的註冊表項下指定檔處理程式的方法。

## <a name="openwithlist-verb"></a>開啟清單謂詞
 當您右鍵單擊 Windows 資源管理員中的檔案時,您將看到 **「打開**」命令。 如果多個產品與擴展關聯,您將看到 **「打開使用」** 子功能表。

 您可以通過在HKEY_CLASSES_ROOT中為檔副檔名設置 OpenWithList 密鑰來註冊不同的應用程式以打開副檔名。 這個鍵下列的檔案副檔名下的應用程式將顯示在「**打開」** 對話框中的 **「建議程式**」標題下。 下面的範例顯示註冊以打開 .vcproj 檔副檔名的應用程式。

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> 指定應用程式的鍵來自HKEY_CLASSES_ROOT_應用程式"下的清單中。

 以新增 OpenWithList 金鑰,您可以聲明應用程式支援檔案副檔名,即使另一個應用程式擁有副檔名。 這可能是應用程式或其他應用程式的未來版本。

## <a name="openwithprogids"></a>開啟與 ProgID
 程式設計識別碼 (ProgID) 是識別應用程式或 COM 物件的版本的類識別的友好版本。 每個可創建物件都應有自己的 ProgID。 例如,VisualStudio.DTE.7.1 啟動 Visual Studio .NET 2003,而 VisualStudio.DTE.10.0 啟動[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 作為項目類型或項目項類型的擁有者,必須為檔擴展名創建特定於版本的 ProgID。 這些 ProgID 可能是冗餘的,因為多個 ProgID 可以啟動相同的應用程式。 有關詳細資訊,請參閱[註冊檔名副檔名的謂詞](../extensibility/registering-verbs-for-file-name-extensions.md)。

 對版本化檔 ProgID 使用以下命名約定,以避免與其他供應商的註冊重複:

|副檔名|版本化 ProgID|
|--------------------|----------------------|
|.擴展|產品名稱。 延伸.version 主要.version 次要|

 通過將版本化 ProgID 作為值添加\\到 HKEY_CLASSES_ROOT*\<副檔名>*_OpenWithProgids 密鑰,可以註冊能夠打開特定檔副檔名的不同應用程式。 此註冊表項包含與檔副檔名關聯的備用 ProgID 的清單。 與列出的 ProgID 關聯的應用程式將顯示在 **「使用**_產品名稱_打開」子功能表中。 如果在`OpenWithList`和`OpenWithProgids`鍵中都指定了相同的應用程式,則操作系統將合併重複項。

> [!NOTE]
> 該`OpenWithProgids`密鑰僅在 Windows XP 中受支援。 由於其他作業系統忽略此密鑰,因此不要將其用作檔處理程式的唯一註冊。 使用此鍵在 Windows XP 中提供更好的用戶體驗。

 將所需的 ProgID 添加為類型REG_NONE的值。 以下代碼提供了註冊檔副檔名 (的 ProgID 的範例(。*ext*)。

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 指定為檔案副檔名的預設值的 ProgID 是預設檔處理程式。 如果修改以前版本附帶[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的檔副檔名的 ProgID,或者可以由其他應用程式接管的檔案擴展名,則必須註冊檔案`OpenWithProgids`擴展名的密鑰,並在清單中指定新的 ProgID 以及您支援的舊 ProgID。 例如：

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 如果舊的 ProgID 具有與其關聯的謂詞,則這些謂詞也會顯示在快捷菜單中的 **「使用***產品名稱*打開」下。

## <a name="see-also"></a>另請參閱
- [關於副檔名](../extensibility/about-file-name-extensions.md)
- [註冊適用於副檔名的動詞命令](../extensibility/registering-verbs-for-file-name-extensions.md)
