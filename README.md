# JAKIM Zone code based on daerah in Malaysia

## Methodology

From JAKIM website: https://www.e-solat.gov.my/, they show the JAKIM Code with their respective districts. I've collected
those information and presents it nicely in MPT-Server site: https://mpt-server.vercel.app/locations.

Now, I need the districts geofences, so that I can determine one's districts given the coordinates. Luckily, I found the districts
geojson file from [nullifye](https://github.com/nullifye): https://github.com/nullifye/malaysia.geojson

The original file is [malaysia.district.geojson](./malaysia.district.geojson), containing this properties for each districts.

```json
"properties": {
    "name": "Baling",
    "code_state": 2,
    "state": "KDH"
},
```

- `name` is the district name, I use this to compare and match with the JAKIM information.
- `code_state` is IC center number
- `state` is a short code for the state. This is not necessarily the same with the initial JAKIM code. But, I use this value to cross check and validate the data I've inputted manually to ensure there are no errors slipped in while in the process of adding the jakim zones data - check [check_zones.py](./check_zones.py)

A copy of the file is created named [malaysia.district-jakim.geojson](./malaysia.district-jakim.geojson). A new item was added to the properties.

```json
"properties": {
    "name": "Kuala Selangor",
    "code_state": 10,
    "state": "SGR",
    "jakim_code": "SGR02"
},
```

Check out Zone Visualization tool - an interactive tool to view map and jakim zones: https://github.com/mptwaktusolat/jakim_zones_map.

## TODOs:

- `Tawau` Sabah. From Jakim list, ada banyak Tawau. Need to check.
- `Sandakan` Sabah. From Jakim list, ada banyak Sandakan. Need to check.
- `Tongod` Sabah not in JAKIM list. Need to make an assumption.
- Add `Bukit Larut` (Perak)
- Add/seperate `Temenggor` & `Belum` (Perak)

## Modification

- `Ulu Langat` (SGR) become `Hulu Langat`
- `Ulu Selangor` (SGR) become `Hulu Selangor`
- Seperated Pulau Aur & Pulau Pemanggil from `Mersing` to individual features.

## Assumptions

Some districts in geojson file doesn't have corresponding match in JAKIM list. I've made some assumptions based on the location of the districts and some data from Internet.

- `Maradong` (Sarawak) set same zone as `Sarikei`. Assumption made based on location of the districts [[wiki]](https://en.wikipedia.org/wiki/Meradong_District).
- `Tanjung Manis` (Sarawak) not in JAKIM list. But found in [JAIS website](https://jais.sarawak.gov.my/web/subpage/webpage_view/150).
- `Asajaya` (Sarawak) set same zone as `Samarahan`. Assumption made based on location of the districts [[wiki]](https://en.wikipedia.org/wiki/Asajaya_District).
- `Pakan` (Sarawak) set same zone as `Sarikei`. Assumption made based on location of the districts [[wiki]](https://en.wikipedia.org/wiki/Pakan,_Sarawak).
- `Selangau` (Sarawak) not in the JAKIM list. Assumption made based on the districts that are on the same longitude axis
- `Tebedu` (Sarawak) not in the JAKIM list. Assumption made based on the districts that are on the same longitude axis
- `Telang Usan` (Sarawak) set same zone as `Miri`. Assumption made based on location of the districts [[wiki]](https://ms.wikipedia.org/wiki/Daerah_Telang_Usan).
- `Subis` (Sarawak) set same zone as `Miri`. Assumption made based on location of the districts [[wiki]](https://en.wikipedia.org/wiki/Subis_District).
- `Beluru` (Sarawak) set same zone as `Miri`. Assumption made based on location of the districts [[wiki]](https://en.wikipedia.org/wiki/Beluru_District).
- `Bukit Mabong` (Sarawak) not in the JAKIM list. Assumption made based on the districts that are on the same longitude axis
- `Hulu Perak` (Perak) not in JAKIM list. Taking information from [Penyelarasan Zon-zon Waktu Solat Seluruh Malaysia](https://www.e-solat.gov.my/portalassets/files/Penyelarasan-Zon-Waktu-Solat.pdf).
- `Batang Padang` (Perak) not in JAKIM list. Taking information from [Penyelarasan Zon-zon Waktu Solat Seluruh Malaysia](https://www.e-solat.gov.my/portalassets/files/Penyelarasan-Zon-Waktu-Solat.pdf).
- `Manjung` (Perak) not in the JAKIM list. Taking information from [Penyelarasan Zon-zon Waktu Solat Seluruh Malaysia](https://www.e-solat.gov.my/portalassets/files/Penyelarasan-Zon-Waktu-Solat.pdf).
- `Kinta` (Perak) not in the JAKIM list. Taking information from [Penyelarasan Zon-zon Waktu Solat Seluruh Malaysia](https://www.e-solat.gov.my/portalassets/files/Penyelarasan-Zon-Waktu-Solat.pdf).
- `Hilir Perak` (Perak) not in the JAKIM list. Taking information from [Penyelarasan Zon-zon Waktu Solat Seluruh Malaysia](https://www.e-solat.gov.my/portalassets/files/Penyelarasan-Zon-Waktu-Solat.pdf).
- `Kerian` (Perak) not in the JAKIM list. Taking information from [Penyelarasan Zon-zon Waktu Solat Seluruh Malaysia](https://www.e-solat.gov.my/portalassets/files/Penyelarasan-Zon-Waktu-Solat.pdf).
- `Larut dan Matang` (Perak) not in the JAKIM list. Taking information from [Penyelarasan Zon-zon Waktu Solat Seluruh Malaysia](https://www.e-solat.gov.my/portalassets/files/Penyelarasan-Zon-Waktu-Solat.pdf).
- `Muallim` not in JAKIM list. Assumption were made from historical data that Muallim was in `Batang Padang` district. [[Wiki]](https://ms.wikipedia.org/wiki/Daerah_Muallim)
