---
title: SccGetProjPath 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: abc7ecf0bb35f61785041d03f871409bbe499854
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434601"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath 函式
此函數會提示使用者輸入專案路徑，也就是只對原始檔控制外掛程式有意義的字串。 使用者時，它會呼叫：

- 建立新的專案

- 將現有專案加入至版本控制

- 嘗試尋找現有的版本控制專案

## <a name="syntax"></a>語法

```cpp
SCCRTN SccGetProjPath (
   LPVOID pvContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPSTR  lpProjName,
   LPSTR  lpLocalPath,
   LPSTR  lpAuxProjPath,
   BOOL   bAllowChangePath,
   LPBOOL pbNew
);
```

### <a name="parameters"></a>參數
 pvContext

[in]原始檔控制外掛程式的內容結構。

 hWnd

[in]原始檔控制外掛程式時，可以使用當做父代上，它會提供任何對話方塊 IDE 視窗的控制代碼。

 lpUser

[in、 out]使用者名稱 （不要超過 SCC_USER_SIZE，包括 NULL 結束字元）

 lpProjName

[in、 out]IDE 專案、 專案工作區中或 makefile （不要超過 SCC_PRJPATH_SIZE，包括 NULL 結束字元） 的名稱。

 lpLocalPath

[in、 out]專案的工作路徑。 如果`bAllowChangePath`是`TRUE`，原始檔控制外掛程式可以修改此字串 （不要超過 _MAX_PATH，包括 null 結束字元）。

 lpAuxProjPath

[in、 out]傳回的專案路徑 （不要超過 SCC_PRJPATH_SIZE，包括 NULL 結束字元） 的緩衝區。

 bAllowChangePath

[in]如果是這`TRUE`，原始檔控制外掛程式可以提示您輸入並修改`lpLocalPath`字串。

 pbNew

[in、 out]傳入的值會指出是否要建立新的專案。 傳回值會指出成功建立專案：

|傳入|解譯|
|--------------|--------------------|
|true|使用者可建立新的專案。|
|false|使用者可能不會建立新的專案。|

|傳出|解譯|
|--------------|--------------------|
|true|建立新的專案。|
|false|選取現有的專案。|

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功建立或擷取專案。|
|SCC_I_OPERATIONCANCELED|已取消作業。|
|SCC_E_ACCESSFAILURE|發生問題，存取原始檔控制系統，可能是因為網路或競爭問題。|
|SCC_E_CONNECTIONFAILURE|發生問題，嘗試連接到原始檔控制系統。|
|SCC_E_NONSPECIFICERROR|發生未指定的錯誤。|

## <a name="remarks"></a>備註
 此函式的目的是取得參數 ide`lpProjName`和`lpAuxProjPath`。 原始檔控制外掛程式會提示使用者提供這項資訊之後，它便會將這兩個字串傳遞回 IDE。 IDE 仍然存在這些字串在其方案檔案，並將它們傳遞至[SccOpenProject](../extensibility/sccopenproject-function.md)每當使用者開啟此專案。 這些字串可讓外掛程式來追蹤與專案相關的資訊。

 第一次呼叫函式，`lpAuxProjPath`設為空字串。 `lProjName` 也可能是空的或包含 IDE 專案名稱，這可能會使用原始檔控制外掛程式，或忽略。 此函式成功傳回時，外掛程式會傳回兩個對應的字串。 IDE 會不做出任何假設這些字串，不會使用它們，並將不允許使用者修改它們。 如果使用者想要變更設定，會呼叫 IDE`SccGetProjPath`同樣地，在相同的值將它傳遞先前的收到先前的時間。 這可讓這兩個字串外掛程式完整控制。

 針對`lpUser`、 IDE 可能會傳入使用者名稱，或它可能只需傳入指標設為空字串。 如果沒有使用者名稱，則原始檔控制外掛程式應該使用它做為預設值。 不過，如果沒有名稱傳遞，或具有指定名稱的登入失敗，外掛程式應該會提示使用者輸入登入和傳遞回名稱`lpUser`當它收到有效的登入。 因為外掛程式可能會變更此字串，IDE 一律會配置大小的緩衝區 (`SCC_USER_LEN`+ 1)。

> [!NOTE]
> IDE 會執行的第一個動作可能會呼叫`SccOpenProject`函式或`SccGetProjPath`函式。 因此，這兩者有相同`lpUser`參數，可讓原始檔控制外掛程式，以將使用者登入兩次。 即使從函式傳回指出失敗，外掛程式必須填妥此使用有效的登入名稱的字串。

 `lpLocalPath` 是，使用者會將專案的目錄。 它可能是空字串。 如果沒有目前定義的 （若為嘗試從原始檔控制系統下載之專案的使用者） 的目錄，而且如果`bAllowChangePath`是`TRUE`，原始檔控制外掛程式可以提示使用者輸入，或使用其他方法，將其擁有字串`lpLocalPath`。 如果`bAllowChangePath`是`FALSE`，外掛程式不應該變更字串，因為使用者已使用指定的目錄中。

 如果使用者建立新的專案，將原始檔控制下，原始檔控制外掛程式可能無法實際建立它在原始檔控制系統中時`SccGetProjPath`呼叫。 相反地，它會傳遞回非零的值給字串`pbNew`，指出將會在原始檔控制系統中建立專案。

 例如，如果中的使用者**新的專案**Visual Studio 中的精靈會將他或她的專案加入至原始檔控制、 Visual Studio 會呼叫此函式，和外掛程式判斷它是否可以在 原始檔控制系統，以建立新的專案包含 Visual Studio 專案。 如果使用者按一下**取消**之前完成精靈，永遠不會建立專案。 如果使用者按一下 **[確定]**，Visual Studio 會呼叫`SccOpenProject`，並傳入`SCC_OPT_CREATEIFNEW`，並在該時間建立原始檔控制專案。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)