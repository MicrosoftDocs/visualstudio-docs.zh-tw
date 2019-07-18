---
title: CA2210:組件應該具備有效的強式名稱 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f94183c6051ed0c2603bbfe35484fabb83a2160f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697992"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210:組件應該具備有效的強式名稱
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|分類|Microsoft.Design|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 未使用強式名稱簽署組件無法驗證強式名稱，或無法有效目前登錄設定的電腦沒有強式名稱。

## <a name="rule-description"></a>規則描述
 此規則會擷取並驗證組件的強式名稱。 如果下列任一項成立，就會發生違規：

- 組件沒有強式名稱。

- 登入後，組件已遭修改。

- 組件是延遲簽章。

- 不正確地簽署組件，或簽署失敗。

- 組件需要登錄設定，才能通過驗證。 比方說，強式名稱工具 (Sn.exe) 用來略過組件的驗證。

  強式名稱可避免用戶端在不知情的狀況下，載入已遭他人修改的組件。 除了極少數的案例以外，您都應該避免部署沒有強式名稱的組件。 如果您共用或散發未正確簽署的組件，表示這個組件或許已遭他人修改，通用語言執行平台可能不會載入組件，或是使用者可能必須停用電腦上的驗證作業。 沒有強式名稱的組件具有下列缺點：

- 無法驗證它的起源。

- Common language runtime 不警告使用者組件的內容已被竄改。

- 它不能載入至全域組件快取。

  請注意，載入和分析的延遲簽署組件，您必須停用組件的驗證。

## <a name="how-to-fix-violations"></a>如何修正違規
 **若要建立金鑰檔案**

 使用下列程序的其中一個：

- 使用所提供的組件連結器工具 (Al.exe) [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK。

- 針對[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]v1.0 或 v1.1，使用任何一種<xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName>或<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>屬性。

- 針對[!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]，使用任何一種`/keyfile`或是`/keycontainer`編譯器選項[/KEYFILE （指定金鑰或金鑰組以簽署組件）](https://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06)或[/KEYCONTAINER （指定金鑰容器以簽署組件）](https://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e)中的連結器選項C++)。

  **若要在 Visual Studio 中以強式名稱組件簽章**

1. 在  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，開啟您的方案。

2. 在 **方案總管**，以滑鼠右鍵按一下您的專案，然後按一下**屬性。**

3. 按一下  **Signing**索引標籤，然後選取**簽署組件**核取方塊。

4. 從**選擇強式名稱金鑰檔**，選取**新增**。

    **建立強式名稱金鑰**視窗會顯示。

5. 在 **金鑰檔名稱**，輸入強式名稱金鑰的名稱。

6. 選擇是否要保護的金鑰與密碼，然後按一下**確定**。

7. 在 **方案總管**，以滑鼠右鍵按一下您的專案，然後按一下**建置**。

   **若要簽署為強式名稱，Visual Studio 外部組件**

- 使用強式名稱工具 (Sn.exe) 所提供的[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]SDK。 如需詳細資訊，請參閱 [Sn.exe (強式名稱工具)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有隱藏此規則的警告，如果環境中使用組件位置竄改內容不是問題。

## <a name="see-also"></a>另請參閱
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
 [如何：簽署為強式名稱組件](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [Sn.exe （強式名稱工具）](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)
