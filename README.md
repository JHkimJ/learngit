# learngit
연습
# h1 입니다.
## h2 입니다.
# MyNames
# coding is so Hard 
## so funny 


----

*글씨체* **글씨체** ***글씨체***

----
```
import React, { useState, useEffect } from "react";
import { useRef } from "react";
import { Map, MapMarker, MapInfoWindow } from 'react-kakao-maps-sdk';
import "./App.css";
// import { Router, Route, Routes } from "react-router-dom";
// import KakaoApi from "./api/MapContainer";
// import Map from "./api/Map copy"

const { kakao } = window;

const App = () => {

  const [coordinates, setCoordinates] = useState(null); // 현재 위치의 좌표값을 저장할 상태
  const mapRef = useRef();

  const getCoordinates = () => {
    const map = mapRef.current;

    setCoordinates({
      center: {
        lat: map.getCenter().getLat(),
        lng: map.getCenter().getLng(),
      },
    });
  };

  const locations = [
    { title: 'DB하이텍 부천캠퍼스', latlng: { lat: 37.5143, lng: 126.7778 } },
    { title: '생태연못', latlng: { lat: 33.450936, lng: 126.569477 } },
    { title: '텃밭', latlng: { lat: 33.450879, lng: 126.56994 } },
    { title: '근린공원', latlng: { lat: 33.451393, lng: 126.570738 } },
  ];
  return (
    <div className="App">
      <div id="map" ></div>
      <Map center={{ lat: 33.450701, lng: 126.570667 }} style={{ margin: 100 , width: '800px', height: '600px' }} level={3}>
        {locations.map((loc, idx) => (
          <MapMarker
            key={`${loc.title}-${loc.latlng}`}
            position={loc.latlng}
            image={{
              src: 'https://t1.daumcdn.net/localimg/localimages/07/mapapidoc/markerStar.png',
              size: { width: 24, height: 35 },
            }}
            title={loc.title}
          />
        ))}
        <MapInfoWindow // 인포윈도우를 생성하고 지도에 표시합니다
          position={{
            // 인포윈도우가 표시될 위치입니다
            lat: 33.450701,
            lng: 126.570667,
          }}
          removable={true} // removeable 속성을 ture 로 설정하면 인포윈도우를 닫을 수 있는 x버튼이 표시됩니다
        >
          {/* 인포윈도우에 표출될 내용으로 HTML 문자열이나 React Component가 가능합니다 */}
          <div style={{ padding: "5px", color: "#000" }}>{ }</div>        </MapInfoWindow>
      </Map>

    </div>

  );
}

export default App;
```
