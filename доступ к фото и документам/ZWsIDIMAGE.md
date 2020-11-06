# ZWsIDIMAGE

Cервис, предоставляющий WEB-сайту информацию о созданных за определенный период фотографиях заданного типа  с дополнительной информацией:
- тип документа основания, к которому прикреплена фотография
- номер документа основания, к которому прикреплена фотография
- завод документа основания, к которому прикреплена фотография 
- пользователь разместивший фотографию

##### ФМ реализующий сервис Z_WS_IDIMAGE

##Входные параметры: 

|Параметр  | Тип            | Опциональность| Описание                                                |
|----------|----------------|---------------|---------------------------------------------------------|
| IT_WERKS | ZWS001_I_WERKS | Optional      | Таблица заводов                                         |
| IS_IDATE | ZWS001_S_IDATE | Required      | Структура с датой размещения фотографии, значение с/по  |
| IT_UTYPE | ZWS001_I_UTYPE | Required      | Таблица типов размещенных фотографии                    |
| IT_DOC1  | ZWS001_I_DOC1  | Optional      | Таблица первичных документов оснований                  |

##Входные параметры:

Параметр    | Тип             | Опциональность| Описание                                               |
------------|-----------------|---------------|--------------------------------------------------------|
 ET_IDIMAGE | ZWS001_I_IDIMAGE| Optional      | Таблица ключей фотографий с дополнительной информацией |
 E_ERROR    | STRING          | Optional      | Текст ошибки                                           |

#
JSON SCHEMA INPUT
```json json_schema
type: object
x-examples:
  example-1:
    IsIdate:
      Begda: string
      Endda: string
    ItDoc1:
      - item:
          Dtype1: string
          Nudoc1: string
    ItUtype:
      - item: string
    ItWerks:
      - item: string
properties:
  IsIdate:
    type: object
    required:
      - Begda
      - Endda
    properties:
      Begda:
        type: string
        minLength: 1
      Endda:
        type: string
        minLength: 1
  ItDoc1:
    type: array
    uniqueItems: true
    minItems: 1
    items:
      type: object
      properties:
        item:
          type: object
          properties:
            Dtype1:
              type: string
              minLength: 1
            Nudoc1:
              type: string
              minLength: 1
  ItUtype:
    type: array
    uniqueItems: true
    minItems: 1
    items:
      type: object
      properties:
        item:
          type: string
          minLength: 1
      required:
        - item
  ItWerks:
    type: array
    uniqueItems: true
    minItems: 1
    items:
      type: object
      properties:
        item:
          type: string
          minLength: 1
required:
  - IsIdate
  - ItUtype

```
#
JSON SCHEMA OUTPUT

```json json_schema
type: object
properties:
  Eerror:
    type: string
    minLength: 1
  EtIdimage:
    type: array
    uniqueItems: true
    minItems: 1
    items:
      type: object
      properties:
        item:
          type: object
          properties:
            Idimg:
              type: string
              minLength: 1
            Wpl:
              type: string
              minLength: 1
            Dtype1:
              type: string
              minLength: 1
            Nudoc1:
              type: string
              minLength: 1
            Dtype2:
              type: string
              minLength: 1
            Nudoc2:
              type: string
              minLength: 1
            Dtype3:
              type: string
              minLength: 1
            Nudoc3:
              type: string
              minLength: 1
            Dwerk:
              type: string
              minLength: 1
            Bname:
              type: string
              minLength: 1
x-examples:
  example-1:
    Eerror: string
    EtIdimage:
      - item:
          Idimg: string
          Wpl: string
          Dtype1: string
          Nudoc1: string
          Dtype2: string
          Nudoc2: string
          Dtype3: string
          Nudoc3: string
          Dwerk: string
          Bname: string

```

#Пример заполнения входных параметров:
```json
       <urn:ZWsIdimage>
         <IsIdate>
            <Begda>01.01.2020</Begda>
            <Endda>31.12.2020</Endda>
         </IsIdate>
         <!--Optional:-->
         <ItDoc1>
            <!--Zero or more repetitions:-->
            <item>
               <Dtype1>08</Dtype1>
               <Nudoc1>7000168449</Nudoc1>
            </item>
         </ItDoc1>
         <ItUtype>
            <!--Zero or more repetitions:-->
            <item>A2</item>
         </ItUtype>
         <!--Optional:-->
         <ItWerks>
            <!--Zero or more repetitions:-->
         </ItWerks>
      </urn:ZWsIdimage>
```

###Пример результирующих данных:
```json
   <n0:ZWsIdimageResponse xmlns:n0="urn:sap-com:document:sap:soap:functions:mc-style">
         <EError/>
         <EtIdimage>
            <item>
               <Idimg>0006389990</Idimg>
               <Wpl>03</Wpl>
               <Dtype1>08</Dtype1>
               <Nudoc1>7000168639</Nudoc1>
               <Dtype2>11</Dtype2>
               <Nudoc2>0001</Nudoc2>
               <Dtype3/>
               <Nudoc3/>
               <Dwerk>7701<Dwerk/>
               <Bname>POLUSHINAES</Bname>
            </item>
         </EtIdimage>
      </n0:ZWsIdimageResponse>
```



