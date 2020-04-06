---
title: 管理並行檔案關聯 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c284fe7ef4c2d07051a8524860583cb634e13bf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702767"
---
# <a name="manage-side-by-side-file-associations"></a>管理並行檔案關聯

如果 VSPackage 提供檔關聯,則必須決定如何處理應呼叫[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的特定版本的並行安裝來打開檔。 不相容的檔案格式使問題複雜化。

使用者希望產品的新版本與早期版本相容,以便可以在新版本中載入現有檔,而不會丟失資料。 理想情況下,VSPackage 可以載入和保存早期版本的檔案格式。 如果事實並非如此,則應提供將檔案格式升級到新版本的 VSPackage。 此方法的缺點是無法在早期版本中打開升級的檔。

為了避免此問題,您可以在檔案格式變得不相容時更改擴展名。 例如,VSPackage 的版本 1 可以使用擴展 *.mypkg10,* 版本 2 可以使用擴展 *.mypkg20*。 此差異識別打開特定檔的 VSPackage。 如果將較新的 VSPackage 添加到與舊擴展名關聯的程式清單中,使用者可以右鍵單擊該檔,並選擇在較新的 VSPackage 中打開該檔。 此時,您的 VSPackage 可以提供將檔案升級到新格式或打開檔並保持與早期版本的 VSPackage 的相容性。

> [!NOTE]
> 您可以組合這些方法。 例如,您可以通過載入較舊的檔案提供向後相容性,並在使用者保存檔案格式時提供升級檔格式。

## <a name="face-the-problem"></a>面對問題

如果希望多個並行 VSPackages 使用相同的延伸,則必須選擇與擴展關聯[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的版本 。 下面是兩個備選方案:

- 在用戶電腦上安裝的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]最新版本中打開該檔。

   在此方法中,安裝程式負責確定 最新[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]版本,包括為檔關聯編寫的註冊表項中的最新版本。 在 Windows 安裝程式包中,可以包括自訂操作來設置指示[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]最新版本 的屬性。

  > [!NOTE]
  > 在此上下文中,"最新"表示"最新支援的版本"。 這些安裝程式條目不會自動檢測[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的後續版本。 [檢測系統要求](../extensibility/internals/detecting-system-requirements.md)和[安裝後必須運行的命令](../extensibility/internals/commands-that-must-be-run-after-installation.md)中的條目與此處介紹的條目類似,並且需要[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]支援的其他版本。

   自定義操作表中的以下行將DEVENV_EXE_LATEST屬性設置為由安裝[後必須在命令](../extensibility/internals/commands-that-must-be-run-after-installation.md)中討論的 AppSearch 和 RegLocator 表設置的屬性。 安裝執行序列表中的行在執行序列的早期計畫自訂操作。 "條件"欄中的值使邏輯工作:

  - Visual Studio .NET 2002 是最新版本,如果它是唯一的當前版本。

  - Visual Studio .NET 2003 是最新版本,[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]僅當它存在 且不存在時。

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]是最新版本,如果它是唯一的當前版本。

    最終結果是,DEVENV_EXE_LATEST包含最新版本 devenv.exe 的路徑。

  **自定義操作表行,確定最新版本的可視化工作室**

  |動作|類型|來源|目標|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **安裝確定最新版本的視覺化工作室的執行序列表行**

  |動作|條件|順序|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002與未(DEVENV_EXE_2003或DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003,而不是DEVENV_EXE_2005|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   您可以使用 Windows 安裝套件註冊表表中的DEVENV_EXE_LATEST屬性編寫**HKEY_CLASSES_ROOT*ProgId*ShellOpenCommand**鍵的預設值 [DEVENV_EXE_LATEST] "%1"

- 運行一個共享啟動程式,可以從可用的 VSPackage 版本做出最佳選擇。

   的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]開發人員選擇這種方法來處理多種格式的解決方案和專案的複雜需求,這些解決方案和專案來自許多版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的 。 在此方法中,您將啟動程式註冊為擴展處理程式。 啟動程式檢查該檔,並決定哪個版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)],您的 VSPackage 可以處理該特定檔。 例如,如果使用者打開上次由 VSPackage 的特定版本保存的檔,啟動[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]器可以在的匹配版本中啟動該 VSPackage。 此外,用戶可以將啟動器配置為始終啟動最新版本。 啟動器還可以提示使用者升級檔的格式。 如果檔案的格式包含版本號,則啟動器可以通知使用者檔案格式是否來自版本,該版本晚於一個或多個已安裝的 VS 包。

   啟動器應位於 Windows 安裝程式元件中,該元件與 VSPackage 的所有版本共用。 此過程可確保始終安裝最新版本,並且在卸載 VSPackage 的所有版本之前不會被刪除。 這樣,即使卸載了一個版本的 VSPackage,也會保留啟動元件的檔關聯和其他註冊表項。

## <a name="uninstall-and-file-associations"></a>卸載和檔案關聯

卸載為檔案關聯寫入註冊表項的 VS 包將刪除檔關聯。 因此,擴展沒有關聯的程式。 Windows 安裝程式不會"恢復"安裝 VSPackage 時添加的註冊表項。 以下是修復使用者檔案關聯的一些方法:

- 使用前面描述的共享啟動元件。

- 指示使用者運行使用者希望擁有文件關聯的 VSPackage 版本的修復。

- 提供單獨的可執行程式,以重寫相應的註冊表項。

- 提供配置選項頁或對話方塊,允許使用者選擇文件關聯並回收丟失的關聯。 指示使用者在卸載後運行它。

## <a name="see-also"></a>另請參閱

- [註冊並行部署的檔案名副檔名](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [註冊檔案名副檔名的謂詞](../extensibility/registering-verbs-for-file-name-extensions.md)
