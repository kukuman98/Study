# eculture-api-note

api.calculations

*  分類item class，根據api.items.xxx

api.item.xxx

* 根據api.params 的 BaseParam取得個別item對應的價格、時間、資訊

api.params

* 分別有：
  *  FeeParam
  *  MPWorkParam
  *  CustomPrice
  *  NumberParam
  *  MultipleParam
  *  SingleParam
* 負責setup param的資料
* default
  *  FEE\_TERMS（fee）
    * 檢查extra terms name 是不是shipping
    * return price
  *  MP\_WORK（wp）
    * 檢查extra terms name是不是mp-work
    * return price
  *  IS\_CUSTOM（is\_custom）
    * 檢查extra terms name是不是special\_offer
    * return true / false
  *  self.total = int\(qty\_sel.value \* qty\_sel.subvalue + process\_sel.value\)
* digital
  *  FEE（fee）
  *  MP（mp）
  *  IS\_CUSTOM（is\_custom）
  *  self.total = \(qty\_sel.value \* page\_sel.value \* material\_sel.value + material\_sel.subvalue +  cover\_sel.value\)
* single
  *  FEE\_TERM（fee\_term）
  *  MPWORK（mp\_work）
  *  IS\_CUSTOM（is\_custom）
  *  self.total = process\_sel.value + material\_sel.value
* size
  *  FEE（fee）
  *  MP（mp）
  *  IS\_CUSTOM（is\_custom）
  *  self.total = （price\_term）term.value + \(process\_select\)proc\_sel.value
* square
  *  TERMS（extra\_price\_terms）
  *  FEE（extra\_price\_terms）
  *  MP（extra\_price\_terms）
  *  self.total = qty\_sel.value \* \(mat\_sel.value + btn\_sel.value\) + proc\_sel.value
* starting
  *  FEE（fee）
  *  MP（mp）
  *  IS\_CUSTOM（is\_custom）
  *  self.total = \(price\_term\)term.value
  *  self.value = \(price\_term.unit\_price\)self.option\["unit\_price"\] \* qty\_sel.value

