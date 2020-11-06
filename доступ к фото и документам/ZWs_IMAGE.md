# ZWs_IMAGE

Cервис, предоставляющий WEB-сайту изображения
##### ФМ реализующий сервис Z_WS_IMAGE

##Входные параметры:

Параметр  | Тип            | Опциональность| Описание                              |
----------|----------------|---------------|---------------------------------------|
 IT_IDIMG | ZWS001_I_IDIMG | Required      | Таблица с идентификаторами фотографий |

##Выходные параметры: 

|Параметр  | Тип            | Опциональность| Описание                                                          
|----------|----------------|---------------|--------------------------------------------------------------------------|
| ET_IMAGE | ZWS001_I_IMAGE | Optional      | Таблица с данными изображений(идентификатор изображения, двоичные данные                                                фотографии, длина файла,текст ошибки) 

#                                       
JSON SCHEMA INPUT

```json json_schema
type: object
properties:
  ItIdimg:
    type: array
    uniqueItems: true
    minItems: 1
    items:
      required:
        - item
      properties:
        item:
          type: string
          minLength: 1
required:
  - ItIdimg
x-examples:
  example-1:
    ItIdimg:
      - item: string
```
#
JSON SCHEMA OUPUT

```json json_schema
type: object
x-examples:
  example-1:
    EtImage:
      - item:
          Idimg: string
          Bin:
            item:
              Line: string
          Length: string
          Error: string
properties:
  EtImage:
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
            Bin:
              type: object
              properties:
                item:
                  type: object
                  properties:
                    Line:
                      type: string
            Length:
              type: string
            Error:
              type: string

```
#Пример заполнения входных параметров:
```json
      <urn:ZWsImage>
         <ItIdimg>
            <item>0006389992</item>
         </ItIdimg>
      </urn:ZWsImage>
```
#Пример результирующих данных:
```json
      <n0:ZWsImageResponse xmlns:n0="urn:sap-com:document:sap:soap:functions:mc-style">
         <EtImage>
            <item>
               <Idimg>7000168449</Idimg>
               <Bin>
                  <item>
                     <Line>
                        RQAUUUUAIaUUUUAFFFGaACiiigAoopDQAuaM01jtGTWXc+JtCspvJutYsYZMkbJJ1U8HHc+oNAGt
                        RWKni3w64O3XdNOOuLpOP1pyeK/D0gymu6aw9rpP8aV0OxsUVmjxBoxXcNVsSOuRcJ/jThruktnb
                        qdm2OuJ1P9aLoVmaFJVRdW05jhb23P0lX/H6/lT/ALfaEZFzEQOOHB+tF0BZFFQ/aYTnEqHHXnpR
                        9oi/56L0z1/z6H8qLoNSajNR+ahGQQfp/n2NHmJzg5x6UXQWZJRTN4xkfpRuHr/9ei6DUfmimhgf
                        zxRuA60wHUZpu4YzmjI9/wAqAHUU3cAPxxRuHr06+1ADqKbuA9aMjNIB1FJuA60mc9KYDqQ0A8d/
                        yoJ+v5UAAooyKM0AFFGaM0agFLmkz/nFFAC0UgpaACiijNABRRmigBMUtFFABRmkNFABSikpaACi
                        iigBMUtFFABRRRQAUUUUAFFFFACYopaSgApRSYpaACiiigAooooAKM0UmKAFooooAKKKKACiiigA
                        ooooATFLRRQAUlLRQAlKKTFLQAUmKWigAooooAKKKKACiiigAzRSYpaAENFBooAWigUUAFFFFABR
                        RRQAUUUZoAKKKKACiiigAooooAKKKKACjNIaKAFooFFABRRRQAUUUUAFFFFABRmkNFAC0UCigAoo
                        ooAKKKKACiiigBMUtFFABRRRQAUUUZoAKKKKACiiigAooooAKKKKACiiigAoozRQAUUUUAFFFFAB
                        RRRQAUUUUAFFFFABRRRQAUUUUAFFFFABRRRmgAooooAKKKKAGL9+n1Gv3zUlABRRRQAUUUUAFFFF
                        ABRRRQAUUUUAFFFFABRRRQAUUUUAFFFFABRRRQAUmKWigAooooAKaWAp1c3441x/Dvhm5v4VVp/l
                        jQHuSfYg5xnv2oA4T4heOnnlXTdEvUCxSnzpoXySRj5cj3zn8u9eY/NuYvltzEknnmgjkFnJySxJ
                        /iJ5J/OneYpG3rimkTcmt1Ro5NqhSF5zjmqr+Uy7fIjUjqQvenRvIkkm5QqbRg45z6Unm+Yoy1MW
                        o13VowWiJQcbcDmooVhNxtMA8uQDIIGVOaFkw7xLISM5CnrT03Y+6CaegJsUosMymNVQ+gHAx0qY
                        FiqBWOB7A1VkYtKOVDIemcZqRbnIztOc/wAIyKmyHckaYrEyAndjadwHI/z/AFoWRnt9jOUbIOdo
                        5HoeOn+J9TTVbc56YFMckuML8ufWjQE2SPdXLBEFw4VcgAgDP1OP85PrRPf3pEccV/eJ8xZtsrDI
                        Ocj8cn/vpvWkU84YgDtk1GJTO0cNqpnlfdtVeS2PQd/pTSTBtotDVtRYSMdX1A8H5jcufXrz0OT...
                        </Line>
                  </item>
               </Bin>
               <Length>408736</Length>
               <Error/>
            </item>
         </EtImage>
      </n0:ZWsImageResponse>
```
