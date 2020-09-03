---
title: CA2210：元件應該有有效的強式名稱 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8f800a550717abfabdfb9296fc8f6de49d127d73
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548196"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210:組件應該具備有效的強式名稱
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|類別|Microsoft. 設計|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 元件未以強式名稱簽署、無法驗證強式名稱，或者如果沒有電腦目前的登錄設定，強式名稱將會無效。

## <a name="rule-description"></a>規則描述
 此規則會抓取並驗證元件的強式名稱。 如果下列任何一項成立，就會發生違規：

- 元件沒有強式名稱。

- 簽署之後，元件已改變。

- 元件已延遲簽署。

- 元件未正確簽署或簽章失敗。

- 元件需要登錄設定才能通過驗證。 例如，強式名稱工具 ( # A0) 用來略過元件的驗證。

  強式名稱可避免用戶端在不知情的狀況下，載入已遭他人修改的組件。 除了極少數的案例以外，您都應該避免部署沒有強式名稱的組件。 如果您共用或散發未正確簽署的組件，表示這個組件或許已遭他人修改，通用語言執行平台可能不會載入組件，或是使用者可能必須停用電腦上的驗證作業。 沒有強式名稱的元件有下列缺點：

- 無法驗證其來源。

- 如果元件的內容已經改變，則 common language runtime 無法警告使用者。

- 它無法載入至全域組件快取。

  請注意，若要載入及分析延遲簽署的元件，您必須停用元件的驗證。

## <a name="how-to-fix-violations"></a>如何修正違規
 **建立金鑰檔**

 您可以使用下列其中一個程序：

- 使用 SDK 所提供的元件連結器工具 ( # A0) [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 。

- 如果是 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 1.0 或 v1.1，請使用 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> 或 <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> 屬性。

- 若是 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] ，請使用 `/keyfile` 或 `/keycontainer` 編譯器選項 [/KEYFILE (指定金鑰或金鑰組來簽署元件) ](https://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06) 或/KEYCONTAINER (在 c + +) 中 [指定金鑰容器以簽署元件) ](https://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e) 連結器選項。

  **若要使用 Visual Studio 中的強式名稱簽署元件**

1. 在中 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，開啟您的方案。

2. 在 **方案總管**中，以滑鼠右鍵按一下您的專案，然後按一下 [ **屬性]。**

3. 按一下 [ **簽署** ] 索引標籤，然後選取 [ **簽署元件** ] 核取方塊。

4. 從 **[選擇強式名稱金鑰**檔] 中選取 [ **新增**]。

    [ **建立強式名稱金鑰** ] 視窗隨即顯示。

5. 在 [ **金鑰檔名稱**] 中，輸入強式名稱金鑰的名稱。

6. 選擇是否要使用密碼來保護金鑰，然後按一下 **[確定]**。

7. 在 **方案總管**中，以滑鼠右鍵按一下您的專案，然後按一下 [ **建立**]。

   **使用外部的強式名稱簽署元件 Visual Studio**

- 使用 SDK 所提供的強式名稱工具 ( # A0) [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 。 如需詳細資訊，請參閱 [Sn.exe (強式名稱工具) ](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有當元件是在不需要考慮內容的環境中使用時，才隱藏此規則的警告。

## <a name="see-also"></a>另請參閱
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
 [如何：使用強式名稱簽署元件](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [Sn.exe (強式名稱工具) ](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)
