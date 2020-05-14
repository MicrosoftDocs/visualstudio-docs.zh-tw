---
title: 服務要點 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e2947cb4cd6a347d8e010340f8689eb1907a28a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705493"
---
# <a name="service-essentials"></a>服務的基本資訊
服務是兩個 VSPackages 之間的協定。 一個 VS 套件為另一個 VSPackage 提供了一組特定的介面。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]本身就是一個 VS 包的集合,它向其他 VS 包提供服務。

 例如,可以使用 SVActivityLog 服務獲取 IVActivityLog 介面,您可以使用該介面寫入活動日誌。 有關詳細資訊,請參閱[:使用活動紀錄](../../extensibility/how-to-use-the-activity-log.md)。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]還提供一些未註冊的內置服務。 VS包可以通過提供服務覆蓋來替換內置服務或其他服務。 任何服務只允許一個服務覆蓋。

 服務沒有可發現性。 因此,您必須知道要使用的服務的服務標識碼 (SID),並且必須知道它提供的介面。 服務的參考文檔提供此資訊。

- 提供服務的 VS 包稱為服務供應商。

- 提供給其他 VSPackages 的服務稱為全域服務。

- 僅對實現它們的 VSPackage 或其創建的任何物件可用的服務稱為本地服務。

- 替換其他包提供的內置服務或服務的服務稱為服務覆蓋。

- 服務或服務覆蓋將按需載入,也就是說,當服務提供者由另一個 VSPackage 請求時載入它。

- 為了支援按需載入,服務提供者將其全域服務註冊到[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 有關詳細資訊,請參閱[如何:提供服務](../../extensibility/how-to-provide-a-service.md)。

- 取得服務後,請使用[查詢介面](/cpp/atl/queryinterface)(非託管代碼)或強制轉換(託管代碼)來取得所需的介面,例如:

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- 託管代碼按服務類型引用服務,而非託管代碼按其 GUID 引用服務。

- 載入[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage 時,它會將服務提供者傳遞到 VSPackage,以便 VSPackage 訪問全域服務。 這稱為 VSPackage 的「坐」。

- VS包可以是它們創建的對象的服務提供者。 例如,表單會向其框架傳送顏色服務的要求,這可能會將請求傳遞[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]給 。

- 深度嵌套或根本不停靠的託管物件可能要求<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>直接訪問全域服務。

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>使用取得全球服務

有時,您可能需要從尚未設置的工具視窗或控制項容器獲取服務,或者已使用不知道所需服務的服務提供者。 例如,您可能希望從控制項內寫入活動日誌。 有關這些方案和其他方案的詳細資訊,請參閱[如何:故障排除服務](../../extensibility/how-to-troubleshoot-services.md)。

您可以通過調用靜<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>態 方法獲得大多數 Visual Studio 服務。

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>依賴於緩存的服務提供者,該提供程式在首次初始化從包派生的任何 VSPackage 時進行定位。 您必須保證滿足此條件,否則必須為 null 服務做好準備。

幸運的是,<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>大多數時候工作正常。

- 如果 VSPackage 提供僅對另一個 VSPackage 已知的服務,則在載入提供服務的 VSPackage 之前,將網站上請求該服務的 VS 包。

- 如果工具視窗由 VSPackage 創建,則在建立工具視窗之前將設定 VSPackage。

- 如果控制容器由 VSPackage 創建的工具視窗承載,則在創建控制項容器之前將 VSPackage 設址。

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>從工具視窗或控制元件容器內取得服務

- 在建構函式、工具視窗或控制的容器中插入此程式碼:

    ```csharp
    IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
        if (log == null) return;
    ```

    ```vb
    Dim log As IVsActivityLog = TryCast(Package.GetGlobalService(GetType(SVsActivityLog)), IVsActivityLog)
    If log Is Nothing Then
        Return
    End If
    ```

    此代碼獲取 SVActivityLog 服務並將其轉換為 IVActivityLog 介面,該介面可用於寫入活動日誌。 有關範例,請參閱[:使用活動紀錄](../../extensibility/how-to-use-the-activity-log.md)。

## <a name="see-also"></a>另請參閱

- [可用服務清單](../../extensibility/internals/list-of-available-services.md)
- [使用和提供服務](../../extensibility/using-and-providing-services.md)
- [轉換和類型轉換](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [轉型](/cpp/cpp/casting)
