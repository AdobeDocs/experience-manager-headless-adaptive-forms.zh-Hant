---
title: Headless最適化Forms的已知問題
description: Headless最適化表單的已知問題。
keywords: headless，最適化表單，已知問題
hide: true
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 16%

---


# 已知問題 {#known-issues}

* 不支援編輯、顯示和資料模式。 (CQ-4327047)
* minItems限制無法動態變更。 (CQ-4342499)
* 違反的面板層級驗證不會擲回任何錯誤。 (CQ-4342373)
* 違反的檔案驗證不會擲回任何錯誤。 (CQ-4342372)
* 自訂屬性不是動態的。 (CQ-4342376)
* 使用運算式在變更事件上動態變更檔案資料會導致無限回圈。 (CQ-4342377)
* 檔案附件不支援說明文字。 (CQ-4342370)
* 如果未選取必要的核取方塊，提交時不會顯示錯誤。 (CQ-4342371)
* aria-label未新增至檔案附件。 (CQ-4341494)
