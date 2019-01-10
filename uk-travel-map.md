---
title: UK Travel Map
layout: page
jumbo_title: UK Travel map
jumbo_text: Premier Inn and Brewdog Bars I've been to...
---

<div id="openseadragon1" style="width: 100%"></div>


<script src="/public/maps/openseadragon.min.js"></script>

<div id="travelmap" style="width: 100%; height: 1500px;"></div>
<script type="text/javascript">
    OpenSeadragon({
        id:            "travelmap",
        defaultZoomLevel: 	1,
        tileSources:   {
            type: 'image',
            url:  '/images/premier-inn-map-nov-17.png'
        }
    });
</script>
<noscript>
    <p>OpenSeadragon is not available unless JavaScript is enabled.</p>
    <img src='/images/premier-inn-map-nov-17.png'
         />
</noscript>
