


App.vue
|
Autocomplete.vue
    <InputForm :data="this"/> //this여기에, address, country등 정보 보냄.

    import {
    // utils.js의 모듈로 된 함수임.
    // 밑에 함수에 this를 전달해 주는데, 이것은 Autocomplete.vue의 data()의 return{}부분의 객체 부분이다.
      queryAutocompleteForSuggestions,
      selectSuggestion,}
|
InputForm.vue
    import inputFields from "../data/input_fields";
    import countries from "../data/countries";

    export default {
      name: "InputForm",

      data() {
        return {
          //inputFields,아래와 같은것. 키와 값이 같을때,
          // 위에 countries"; 임포트한 것을 컴포넌트로만 쓰는게 아니라,
          countries";의 데이터를 InputForm.vue에서도 쓸때도 사용한다.
          inputFields : inputFields,
          // countries,
          countries : countries
        };

-------------
utils.js에
export function formatSuggestion(suggestion, country) {}
export function queryAutocompleteForSuggestions(query) {
}
// countries[0]는 {name:"United States", iso2:"US"} 임.
if (! this.country.iso2) this.country = countries[0];
<-- 위의 this는 queryAutocompleteForSuggestions호출하는 것의 객체인 듯.
}
등 함수를 모듈로 사용하게 위해, 정의해놈.

---------
Country.js에서

export default class Country {

    constructor(name, iso2) {
        this.name = name;
        this.iso2 = iso2;
    }
}
----
countries.js에서
<-- 아주 많은 나라가, name, iso2 필드를 가지게 하고,
country={name:"United States", iso2:"US"}
이런식의 객체를 아주 많이 만들때, class로 객체를 생성하는 것.

import Country from "./models/Country";

export const countries = [
    new Country("United States", "US"),
    ...];
