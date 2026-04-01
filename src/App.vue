<script setup>
import { computed, reactive, ref } from 'vue'

const categories = [
  { label: 'Guitarras', hint: 'Tono de élite, cuerpo impecable' },
  { label: 'Pianos', hint: 'Mecánica exquisita, resonancia total' },
  { label: 'Bajos', hint: 'Graves definidos, energía estable' },
  { label: 'Baterías', hint: 'Golpe premium, control total' },
  { label: 'Micrófonos', hint: 'Captura detallada, aire de estudio' },
  { label: 'Interfaces', hint: 'Conversión limpia, control total' },
  { label: 'GOLD PACKS', hint: 'Soluciones reales para producción', extra: true },
  { label: 'Convenios de estudios', hint: 'Descuentos en estudios de élite', extra: true },
]

const guitarTypes = [
  { label: 'Eléctricas', hint: 'Potencia y presencia total' },
  { label: 'Hollow', hint: 'Cuerpo amplio y orgánico' },
  { label: 'Electroacústicas', hint: 'Resonancia premium amplificada' },
  { label: 'Nylon', hint: 'Calidez clásica y tacto fino' },
]

const pianoTypes = [
  { label: 'Cola', hint: 'Concert grand absoluto' },
  { label: 'Digitales', hint: 'Stage y estudio premium' },
  { label: 'Controladores', hint: 'Flujo creativo, tacto preciso' },
]

const bassTypes = [
  { label: 'Eléctricos', hint: 'Definición y pegada total' },
  { label: 'Acústicos', hint: 'Resonancia orgánica premium' },
]

const micTypes = [
  { label: 'Estudio', hint: 'Referencia absoluta de estudio' },
  { label: 'Voz', hint: 'Voces y versatilidad total' },
]

const guitarProducts = {
  Eléctricas: [
    {
      name: 'Fender American Professional II Stratocaster',
      image:
        'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774031987/Fender_American_Professional_II_Stratocaster_jaady2.png',
      why: [
        'Estándar histórico del sonido eléctrico moderno',
        'Versatilidad total en estudio y directo',
      ],
      use: ['David Gilmour', 'John Mayer', 'Eric Clapton'],
      tracks: ['Comfortably Numb', 'Money'],
      build: ['Cuerpo de alder', '3 single-coils', 'Escala 25.5"', 'Bolt-on neck'],
      price: 'USD $1.950',
    },
    {
      name: 'Gibson Les Paul Standard',
      image:
        'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774032068/Gibson_Les_Paul_Standard_ufmgaw.png',
      why: ['Sustain y grosor tonal inigualable', 'Referencia absoluta en rock'],
      use: ['Jimmy Page', 'Slash'],
      tracks: ['Whole Lotta Love', "Sweet Child O' Mine"],
      build: ['Cuerpo mahogany + maple top', 'Set-neck', 'Humbuckers'],
      price: 'USD $3.000',
    },
    {
      name: 'PRS Custom 24',
      image:
        'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774032057/PRS_Custom_24_gvdyrn.png',
      why: ['Mezcla entre Fender y Gibson', 'Extremadamente versátil'],
      use: ['Carlos Santana', 'Mark Tremonti'],
      tracks: [],
      build: ['24 trastes', 'Coil split', 'Tremolo PRS'],
      price: 'USD $4.500',
    },
    {
      name: 'Ibanez JEM7V',
      image:
        'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774031971/Ibanez_JEM7V_k3obeh.png',
      why: ['Referencia absoluta en guitarra técnica'],
      use: ['Steve Vai'],
      tracks: ['For the Love of God'],
      build: ['Floyd Rose', 'Neck ultradelgado', 'Acceso extremo a trastes altos'],
      price: 'USD $2.850',
    },
    {
      name: 'Ernie Ball Music Man Majesty (John Petrucci)',
      image:
        'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774031957/Ernie_Ball_Music_Man_Majesty_John_Petrucci_f6ftnp.png',
      why: ['Precision quirurgica para metal/prog moderno'],
      use: ['John Petrucci'],
      tracks: ['Pull Me Under'],
      build: ['Piezo + humbuckers', 'Ergonomia extrema', 'Electronica avanzada'],
      price: 'USD $4.000',
    },
  ],
  Hollow: [
    {
      name: 'Gibson ES-335',
      image:
        'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774031989/gibson_es_335_c8uobl.png',
      why: ['Balance perfecto entre sólido y resonancia'],
      use: ['Larry Carlton', 'B.B. King'],
      tracks: [],
      build: ['Bloque central', 'Semi-hollow'],
      price: 'USD $3.500',
    },
    {
      name: 'Gibson ES-175',
      image:
        'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774032047/Gibson_ES-175_amzwht.png',
      why: ['Estándar jazz clásico'],
      use: ['Joe Pass'],
      tracks: [],
      build: ['Hollow completo', 'Sonido calido y profundo'],
      price: 'USD $5.500',
    },
    {
      name: 'Gretsch White Falcon',
      image:
        'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774031994/gretsch_white_falcon_mflaez.png',
      why: ['Icono visual y tonal'],
      use: ['Brian Setzer'],
      tracks: [],
      build: ['Hollow grande', 'FilterTron pickups'],
      price: 'USD $4.250',
    },
    {
      name: 'PRS Hollowbody II',
      image:
        'https://www.stars-music.com/medias/prs/cropped-hollowbody-ii-piezo-usa-2h-ht-eb-230365749-215771.png',
      why: ['Hollow moderno sin problemas de feedback'],
      use: [],
      tracks: [],
      build: ['Tallado solido', 'Piezo integrado'],
      price: 'USD $5.250',
    },
    {
      name: 'Ibanez GB10',
      image:
        'https://www.ibanez.com/common/product_artist_file/file/p_region_GB10_BS_00_09.png',
      why: ['Jazz profesional compacto'],
      use: ['George Benson'],
      tracks: [],
      build: ['Tamano reducido', 'Menos feedback'],
      price: 'USD $3.000',
    },
  ],
  Electroacústicas: [
    {
      name: 'Taylor 814ce',
      image:
        'https://www.taylorguitars.com/sites/default/files/styles/twitter_card/public/2022-02-08/814ceN-Front.png.webp?h=99356be3&itok=jyCZm3Hp',
      why: ['Precision y afinacion perfecta en vivo'],
      use: ['Taylor Swift'],
      tracks: [],
      build: ['V-Class bracing'],
      price: 'USD $4.000',
    },
    {
      name: 'Martin D-28',
      image:
        'https://www.stars-music.com/medias/martin-guitar/cropped-custom-shop-expert-d-28-1937-epicea-palissandre-eb-2747363-205366.png',
      why: ['Estándar acústico histórico'],
      use: ['Neil Young', 'Bob Dylan'],
      tracks: [],
      build: ['Rosewood + spruce', 'Graves profundos'],
      price: 'USD $3.500',
    },
    {
      name: 'Gibson J-45',
      image: 'https://www.stars-music.com/medias/gibson/cropped-j-45-standard-modern-dreadnought-epicea-acajou-rw-217510.png',
      why: ['Sonido calido y vintage'],
      use: ['John Lennon'],
      tracks: [],
      build: [],
      price: 'USD $3.000',
    },
    {
      name: 'Yamaha FG9',
      image:
        'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774032028/yamaha_fg9_ljcez4.png',
      why: ['Precision japonesa de concierto'],
      use: [],
      tracks: [],
      build: [],
      price: 'USD $4.000',
    },
    {
      name: 'Taylor K24ce',
      image:
        'https://www.taylorguitars.com/sites/default/files/styles/twitter_card/public/2022-02-08/Builders%20Edition%20K24ce-Front.png.webp?h=99356be3&itok=pozv7ZKE',
      why: ['Madera koa premium, tono unico'],
      use: [],
      tracks: [],
      build: [],
      price: 'USD $5.500',
    },
  ],
  Nylon: [
    {
      name: 'Ramirez 1a',
      image:
        'https://www.siccasguitars.com/cdn/shop/files/a-joseramirez-1AKlassik-1969-06032020-1.png?v=1758651474',
      why: ['Referencia absoluta espanola'],
      use: ['Andres Segovia'],
      tracks: [],
      build: [],
      price: 'USD $9.000',
    },
    {
      name: 'Yamaha GC82',
      image:
        'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774031988/yamaha_gc82_o5ueok.png',
      why: ['Precision de concierto'],
      use: [],
      tracks: [],
      build: [],
      price: 'USD $7.000',
    },
    {
      name: 'Cordoba Master Series',
      image: 'https://cordobaguitars.com/image/cache/catalog/guitars/c1m/1-1755x998.webp',
      why: ['Luthieria tradicional accesible'],
      use: [],
      tracks: [],
      build: [],
      price: 'USD $4.000',
    },
    {
      name: 'Alhambra 11P',
      image: 'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774036367/Alhambra_11p_ajuyau.png',
      why: ['Balance profesional/precio'],
      use: [],
      tracks: [],
      build: [],
      price: 'USD $2.500',
    },
    {
      name: 'Godin Multiac Nylon',
      image: 'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774032013/godin_multiac_nryphz.png',
      why: ['Mejor nylon para escenario'],
      use: ['Al Di Meola'],
      tracks: [],
      build: ['Sistema híbrido (eléctrica + nylon)'],
      price: 'USD $2.000',
    },
  ],
}

const pianoProducts = {
  Cola: [
    {
      name: 'Steinway & Sons Model D (D-274)',
      image:
        'https://hinves.com/wp-content/uploads/2013/05/piano-cola-steinway-sons-d274-artesanal-nuevo-negro-picada-1200x820.png',
      why: ['Estándar mundial de concierto', 'Referencia absoluta en grabación'],
      use: ['Lang Lang', 'Van Cliburn Competition'],
      tracks: ['Repertorio clásico completo'],
      build: ['12.000 piezas', 'Soundboard diaphragmatic', 'Marco rigido'],
      price: 'USD $175.000',
    },
    {
      name: 'Bosendorfer 290 Imperial',
      image: 'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774031957/bosendorfer_290_imperial_yzqjrv.png',
      why: ['97 teclas, rango extendido', 'Sonido profundo y orquestal'],
      use: ['Liszt', 'Ravel', 'Debussy'],
      tracks: [],
      build: ['Caja de resonancia tipo violín', 'Graves extendidos reales'],
      price: 'USD $325.000',
    },
    {
      name: 'Fazioli F308',
      image: 'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774032001/fazioli_f308_xy7unz.png',
      why: ['Piano más hi-fi del mercado', 'Preferido en grabaciones modernas'],
      use: ['Herbie Hancock'],
      tracks: ['Jazz contemporaneo'],
      build: ['Longitud 3.08m', 'Maderas seleccionadas'],
      price: 'USD $240.000',
    },
    {
      name: 'Yamaha CFX',
      image: 'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774031962/yamaha_cfx_zuidtf.png',
      why: ['Consistencia y precision japonesa'],
      use: ['Chopin Competition'],
      tracks: ['Clasicos contemporaneos'],
      build: ['Sonido brillante y definido', 'Accion controlable'],
      price: 'USD $150.000',
    },
    {
      name: 'Shigeru Kawai SK-EX',
      image: 'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774031999/Shigeru_Kawai_SK-EX_wdkjua.png',
      why: ['Handmade japones ultra premium'],
      use: ['Tchaikovsky Competition'],
      tracks: [],
      build: ['Producción limitada', 'Ajuste manual artesanal'],
      price: 'USD $160.000',
    },
  ],
  Digitales: [
    {
      name: 'Yamaha CP88',
      image: 'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774031966/yamaha_cp88_nt4tv7.png',
      why: ['Diseñado para directo profesional'],
      use: ['Stage players', 'Worship', 'Touring'],
      tracks: [],
      build: ['Motor CFX + Bosendorfer samples', 'Teclado NW-GH'],
      price: 'USD $2.750',
    },
    {
      name: 'Nord Stage 4',
      image: 'https://bolpianos.com/cdn/shop/files/KNO-NS4-73-B.png?v=1685359297&width=2048',
      why: ['Estandar absoluto en escenarios'],
      use: ['Worship', 'Pop', 'Touring mundial'],
      tracks: [],
      build: ['Secciones piano/synth/organ'],
      price: 'USD $5.250',
    },
    {
      name: 'Roland RD-2000',
      image: 'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774031955/roland_rd2000_r4ijcx.png',
      why: ['Motor híbrido modelado + sample'],
      use: [],
      tracks: [],
      build: ['Teclado PHA-50', 'Baja latencia'],
      price: 'USD $2.750',
    },
    {
      name: 'Kawai MP11SE',
      image: 'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774032036/Kawai_MP11SE_otb5nz.png',
      why: ['El más cercano a piano acústico'],
      use: [],
      tracks: [],
      build: ['Accion con piezas de madera reales'],
      price: 'USD $3.150',
    },
    {
      name: 'Dexibell VIVO S10',
      image: 'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774031981/Dexibell_VIVO_S10_e2zaqq.png',
      why: ['Modelado realista avanzado'],
      use: [],
      tracks: [],
      build: ['T2L sound engine', 'Alta fidelidad'],
      price: 'USD $2.500',
    },
  ],
}

const controllerProducts = [
  {
    name: 'Native Instruments Komplete Kontrol S88 MK2',
    image:
      'https://media.sweetwater.com/m/products/image/c899897754cunssGaKUAhpla7O3q3CIlvJDTovw8.wm-lw.png?quality=82&width=750&ha=c899897754cdef0a',
    why: ['Integracion total con DAW + plugins', 'Ecosistema profesional completo'],
    use: ['Workflow Hans Zimmer'],
    tracks: ['Producción moderna'],
    build: ['Teclado Fatar', 'Pantallas integradas'],
    price: 'USD $1.300',
  },
  {
    name: 'Arturia KeyLab 88 MkII',
    image: 'https://cdn.long-mcquade.com/files/431703/3f364eea52647792633bbe56988b2dcb.png',
    why: ['Control total y construccion premium'],
    use: ['Producción híbrida'],
    tracks: [],
    build: ['Teclado Fatar hammer action', 'Pads + faders + DAW control'],
    price: 'USD $1.050',
  },
  {
      name: 'Akai MPK261',
      image:
        'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774032012/Akai_MPK261_heoybm.png',
    why: ['Producción beat y performance'],
    use: ['Hip-hop', 'Electronica'],
    tracks: [],
    build: ['Pads MPC', 'Control completo DAW'],
    price: 'USD $600',
  },
  {
      name: 'Novation SL MkIII',
      image: 'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774037141/Novation_SL_MkIII_1_xzu9a1.png',
    why: ['Integracion hardware + software'],
    use: ['Live performance', 'Synth rigs'],
    tracks: [],
    build: ['Secuenciador integrado', 'CV/Gate outputs'],
    price: 'USD $800',
  },
  {
    name: 'M-Audio Hammer 88 Pro',
    image:
      'https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/69050280802/original/AhKvC3KCTC3d91e_HA17AjAey8rkN8G9xQ.png?1665178473',
    why: ['Mejor relacion precio/teclado pesado'],
    use: ['Pianistas en escenario'],
    tracks: [],
    build: ['Hammer action realista'],
    price: 'USD $750',
  },
]

const goldPacks = [
  {
    name: 'GOLD PACK 1 — STUDIO POP PROFESIONAL',
    focus: 'Producción moderna, limpia, lista para radio.',
    instruments: ['Fender Stratocaster', 'Fender Jazz Bass', 'Yamaha CP88', 'Yamaha Recording Custom'],
    mic: 'Neumann U87 Ai',
    interface: 'Universal Audio Apollo x16',
    narrative:
      'Un setup diseñado para lograr producciones modernas con claridad, definición y balance. Cada instrumento está pensado para ocupar su espacio en la mezcla sin conflicto. Desde voces hasta batería, todo está optimizado para grabación profesional.',
    hook: 'El sonido que escuchas en la radio, en un solo paquete',
  },
  {
    name: 'GOLD PACK 2 — ROCK CLÁSICO / ANALÓGICO',
    focus: 'Rock con caracter, cuerpo y presencia.',
    instruments: ['Gibson Les Paul Standard', 'Fender Precision Bass', 'Yamaha CP88', 'Gretsch USA Custom'],
    mic: 'Telefunken U47',
    interface: 'Apogee Symphony I/O Mk II',
    narrative:
      'Este pack está construido para capturar el sonido del rock en su forma más pura. Graves sólidos, guitarras densas y una batería con identidad. Es un setup que no busca perfección digital, sino carácter real.',
    hook: 'El sonido del rock como debe ser: crudo, real, inolvidable',
  },
  {
    name: 'GOLD PACK 3 — JAZZ / FUSIÓN DE ALTO NIVEL',
    focus: 'Dinamica, detalle y musicalidad.',
    instruments: ['Gibson ES-335', 'Ibanez GB10', 'Kawai MP11SE', 'Gretsch USA Custom'],
    mic: 'AKG C414 XLII',
    interface: 'Prism Sound Atlas',
    narrative:
      'Diseñado para capturar cada matiz, cada respiración, cada intención musical. Este pack permite trabajar con dinámica real, donde el instrumento responde al intérprete sin compresión artificial.',
    hook: 'Cuando cada nota importa',
  },
  {
    name: 'GOLD PACK 4 — PRODUCCIÓN MODERNA / URBANO',
    focus: 'Hip-hop, R&B, pop moderno.',
    instruments: ['PRS Custom 24', 'Music Man StingRay', 'Nord Stage 4', 'Tama Starclassic Maple'],
    mic: 'Sony C-800G',
    interface: 'Antelope Orion',
    narrative:
      'Este pack está orientado a producciones actuales donde la claridad vocal y el impacto rítmico son clave. Desde beats hasta instrumentos en vivo, todo está pensado para sonar moderno y competitivo.',
    hook: 'Sonido listo para plataformas, desde el primer take',
  },
  {
    name: 'GOLD PACK 5 — ACÚSTICO / CINEMÁTICO',
    focus: 'Producción emocional, orgánica.',
    instruments: ['Taylor 814ce', 'Godin Multiac Nylon', 'Steinway Model D', 'Yamaha Recording Custom'],
    mic: 'Telefunken ELA M 251',
    interface: 'RME Fireface UFX',
    narrative:
      'Un entorno diseñado para capturar emoción real. Maderas, aire, dinámica natural. Este pack prioriza la profundidad sonora y la interpretación por sobre la producción artificial.',
    hook: 'Cuando la musica se siente, no se procesa',
  },
]

const studioDeals = [
  {
    name: 'Abbey Road Studios',
    location: 'Londres, Reino Unido',
    images: [
      'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774049217/abbeyroad_1_szfbjp.avif',
      'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774049205/abbeyroad_2_p8tt5l.jpg',
      'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774049213/abbeyroad_3_povgxe.jpg',
      'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774049204/abbeyroad_4_azm8mi.jpg',
    ],
    why: [
      'Es probablemente el estudio mas influyente de la historia',
      'Referencia en grabación orquestal, rock y cine',
    ],
    productions: ['The Beatles', 'Pink Floyd', 'Bandas sonoras (Star Wars, Harry Potter)'],
    technical: ['Salas acústicas legendarias', 'Consolas y equipamiento híbrido (analógico + digital)'],
    claim: 'Este no es un estudio, es un estándar mundial.',
  },
  {
    name: 'Capitol Studios',
    location: 'Los Angeles, EE.UU.',
    images: [
      'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774049264/capitol_1_vq5voj.jpg',
      'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774049239/capitol_2_avqyia.jpg',
      'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774049241/capitol_3_vowbnw.webp',
      'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774049237/capitol_4_wjddpt.webp',
    ],
    why: ['Famoso por sus echo chambers subterraneos unicos', 'Sonido vocal de referencia historica'],
    productions: ['Frank Sinatra', 'Nat King Cole', 'Producciones modernas de alto nivel'],
    technical: ['Acústica diseñada desde cero', 'Sonido vocal inigualable'],
  },
  {
    name: 'Electric Lady Studios',
    location: 'Nueva York, EE.UU.',
    images: [
      'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774049247/electric_1_dq7xkb.jpg',
      'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774049243/electric_2_jnczic.jpg',
      'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774049250/electric_3_dqcokm.jpg',
      'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774049246/electric_4_cpzobu.jpg',
    ],
    why: ['Diseñado por Jimi Hendrix', 'Enfoque artístico + técnico'],
    productions: ['Jimi Hendrix', 'Daft Punk', 'Kanye West'],
    technical: ['Entorno creativo + tecnologia de alto nivel', 'Estudio pensado para artistas, no solo ingenieros'],
  },
  {
    name: 'Ocean Way Recording (United Recording)',
    location: 'Los Angeles / Nashville',
    images: [
      'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774049256/ocean_1_uxama7.jpg',
      'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774049252/ocean_2_lllgg2.jpg',
      'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774049254/ocean_3_wyqark.jpg',
      'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774049258/ocean_4_x6e0ms.jpg',
    ],
    why: ['Una de las mejores salas de grabación del mundo', 'Ideal para bandas completas y orquesta'],
    productions: ['Radiohead', 'Red Hot Chili Peppers', 'Film scoring'],
    technical: ['Espacios grandes, sonido natural real', 'Equipamiento analógico de primer nivel'],
  },
  {
    name: 'Blackbird Studio',
    location: 'Nashville, EE.UU.',
    images: [
      'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774049235/blackbird_1_zhusmw.jpg',
      'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774049221/blackbird_2_b0vacx.webp',
      'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774049223/blackbird_3_bdcx5e.jpg',
      'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774049231/blackbird_4_agqsm5.webp',
    ],
    why: ['Uno de los estudios mejor equipados del mundo', 'Coleccion masiva de microfonos y consolas'],
    productions: ['Taylor Swift', 'Kings of Leon', 'Musica country y pop de alto nivel'],
    technical: ['Múltiples salas optimizadas', 'Flexibilidad total de producción'],
  },
]

const bassProducts = {
  Eléctricos: [
    {
      name: 'Fender Precision Bass (American / Custom Shop)',
      image:
        'https://www.basscentre.com.au/cdn/shop/files/0190160805_fen_ins_frt_1_rr_5000x.png?v=1750650796',
      why: ['El bajo mas grabado de la historia', 'Define el sonido en rock, pop y gospel'],
      use: ['James Jamerson', 'Pino Palladino', 'Nate Mendel'],
      tracks: ['Wherever I Lay My Hat'],
      build: ['1 split-coil pickup', 'Cuerpo alder', 'Escala 34"'],
      price: 'USD $2.750',
    },
    {
      name: 'Music Man StingRay Special',
      image:
        'https://s3-us-west-2.amazonaws.com/static.music-man.com/website/images/instruments/instrument-132.png?1771996080',
      why: ['Primer bajo con EQ activo integrado', 'Sonido moderno que corta mezcla'],
      use: ['Flea', 'Louis Johnson', 'Pino Palladino'],
      tracks: [],
      build: ['Humbucker + preamp activo', 'Ataque agresivo y definido', 'Muy versátil'],
      price: 'USD $3.000',
    },
    {
      name: 'Fender Jazz Bass',
      image:
        'https://www.clipartmax.com/png/full/293-2938349_bass-guitar-png-transparent-images-fender-70s-jazz-bass.png',
      why: ['Más versátil que el Precision', 'Ideal para slap, jazz, fusión'],
      use: ['Jaco Pastorius', 'Marcus Miller'],
      tracks: ['Portrait of Tracy'],
      build: ['2 single-coils', 'Sonido definido y articulado'],
      price: 'USD $2.500',
    },
    {
      name: 'Rickenbacker 4003',
      image: 'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774031972/rickenbacker_kehdjp.png',
      why: ['Sonido unico, agresivo y reconocible'],
      use: ['Paul McCartney', 'Geddy Lee', 'Lemmy'],
      tracks: [],
      build: ['Neck-through', 'Pastillas con caracter brillante'],
      price: 'USD $2.500',
    },
    {
      name: 'Fodera Emperor (Custom)',
      image: 'https://www.guitar-planet.co.uk/wp-content/uploads/2017/09/Fodera-Imperial-Premium.png',
      why: ['Nivel boutique, instrumento de autor'],
      use: ['Victor Wooten', 'Anthony Jackson'],
      tracks: [],
      build: ['Hecho a mano', 'Maderas exoticas', 'Electronica custom'],
      price: 'USD $11.500',
    },
  ],
  Acústicos: [
    {
      name: 'Tacoma Thunderchief (CB10 / CB105)',
      image:
        'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774031961/Tacoma_Thunderchief_CB10___CB105_e6aclp.png',
      why: ['El bajo acústico más respetado históricamente'],
      use: ['Folk', 'Unplugged profesional'],
      tracks: [],
      build: ['Caja grande real', 'Sonido profundo sin amplificacion'],
      price: 'USD $3.000',
    },
    {
      name: 'Taylor GS Mini Bass',
      image:
        'https://www.taylorguitars.com/sites/default/files/styles/twitter_card/public/images/2024-09/Taylor-GS%20Mini-e-Special-Edition-Sunset-Fade-2211073429-FrontLeft-2024.png.webp?h=99356be3&itok=J5RWC5UX',
      why: ['El mas usable en contexto real'],
      use: ['Producción acústica moderna'],
      tracks: [],
      build: ['Escala corta', 'Pastillas integradas'],
      price: 'USD $850',
    },
    {
      name: 'Martin BC-16E',
      image:
        'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774031982/Martin_BC-16E_dtysdl.png',
      why: ['Calidad Martin aplicada a bajo acústico'],
      use: [],
      tracks: [],
      build: ['Spruce + rosewood', 'Sonido calido y profundo'],
      price: 'USD $2.150',
    },
    {
      name: 'Ibanez AEB10 / AEB Series',
      image:
        'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774031978/Ibanez_AEB10___AEB_Series_blnwuu.png',
      why: ['Estandar moderno accesible'],
      use: [],
      tracks: [],
      build: ['Preamp integrado', 'Cuerpo comodo'],
      price: 'USD $500',
    },
    {
      name: 'Godin A4 Ultra (Semi-acustico)',
      image:
        'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774031976/Godin_A4_Ultra_Semi-acustico_vwpcbz.png',
      why: ['Solucion profesional para escenario'],
      use: ['Jazz', 'Fusion', 'Directo'],
      tracks: [],
      build: ['Cuerpo chambered', 'Piezo + electrónica avanzada'],
      price: 'USD $2.000',
    },
  ],
}

const micProducts = {
  Estudio: [
    {
      name: 'Neumann U87 Ai',
      image:
        'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774032018/Neumann_U87_Ai_giyx1q.png',
      why: ['Micrófono más usado en estudios profesionales', 'Funciona en casi cualquier fuente'],
      use: ['Paul McCartney', 'Ed Sheeran', 'Michael Jackson'],
      tracks: [],
      build: ['Condensador FET multipatron', 'Respuesta balanceada', 'Mix-ready'],
      price: 'USD $3.600',
    },
    {
      name: 'Sony C-800G',
      image: 'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774032007/Sony_C-800G_i4ho59.png',
      why: ['El vocal mas usado en hip-hop y pop moderno', 'Claridad extrema en agudos'],
      use: ['Dr. Dre productions', 'Mariah Carey', 'Drake'],
      tracks: [],
      build: ['Tubo + sistema de enfriamiento', 'Ultra alta definición'],
      price: 'USD $13.500',
    },
    {
      name: 'Telefunken U47 (Reissue)',
      image: 'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774032042/Telefunken_U47_Reissue_wljz6w.png',
      why: ['Icono historico de estudio', 'Peso en medios graves'],
      use: ['Frank Sinatra', 'The Beatles'],
      tracks: [],
      build: ['Tubo', 'Sonido con cuerpo'],
      price: 'USD $10.000',
    },
    {
      name: 'Telefunken ELA M 251E',
      image:
        'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774031995/Telefunken_ELA_M_251E_xmt7sz.png',
      why: ['Uno de los mejores mics vocales jamas creados', 'Agudos suaves y aireados'],
      use: ['Voces pop femeninas high-end'],
      tracks: [],
      build: ['Tubo premium', 'Sonido lujoso'],
      price: 'USD $12.500',
    },
    {
      name: 'AKG C414 XLII',
      image: 'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774032026/AKG_C414_XLII_wxfmgu.png',
      why: ['Micrófono versátil de referencia', 'Multi-herramienta de estudio'],
      use: ['Drum overheads', 'Piano', 'Voces'],
      tracks: [],
      build: ['9 patrones polares', 'Alta precision'],
      price: 'USD $1.500',
    },
  ],
  Voz: [
    {
      name: 'Shure SM7B',
      image: 'https://castel.cl/80-large_default/shure-sm7b.jpg',
      why: ['Uno de los mics más versátiles de la historia', 'Funciona en salas no tratadas'],
      use: ['Michael Jackson', 'Podcasts', 'Streaming'],
      tracks: ['Billie Jean'],
      build: ['Dinamico', 'Rechazo de ruido ambiente'],
      price: 'USD $425',
    },
    {
      name: 'Electro-Voice RE20',
      image: 'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774031968/Electro-Voice_RE20_vyvebg.png',
      why: ['Ultra versátil para voz y broadcast'],
      use: ['Broadcast profesional', 'Producción vocal'],
      tracks: [],
      build: ['Tecnologia Variable-D', 'Sonido limpio y controlado'],
      price: 'USD $500',
    },
    {
      name: 'Neumann TLM 103',
      image: 'https://www.gothamsound.com/sites/default/files/Neumann_TLM-103-with-EA1_Neumann-Studio-Microphone_M.png',
      why: ['Version mas accesible del U87'],
      use: ['Voces modernas', 'Home studio pro'],
      tracks: [],
      build: ['Condensador cardioide', 'Mayor presencia en agudos'],
      price: 'USD $1.250',
    },
    {
      name: 'Shure SM58',
      image:
        'https://cdn11.bigcommerce.com/s-8f505/images/stencil/original/products/4337/37387/SM58-4__75236.1666638686.png?c=2',
      why: ['El microfono vocal mas usado en la historia'],
      use: ['Escenarios en vivo'],
      tracks: [],
      build: ['Dinamico', 'Ultra resistente'],
      price: 'USD $125',
    },
    {
      name: 'Universal Audio Sphere DLX',
      image: 'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774032005/Universal_Audio_Sphere_DLX_exf3dm.png',
      why: ['Modela multiples microfonos legendarios'],
      use: ['Producción moderna híbrida'],
      tracks: [],
      build: ['Dual capsule', 'Software modeling'],
      price: 'USD $1.750',
    },
  ],
}

const interfaceProducts = [
  {
    name: 'Universal Audio Apollo x16 Gen 2',
    image: 'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774031960/Universal_Audio_Apollo_x16_Gen_2_idwe5y.png',
    why: ['Estándar en estudios híbridos', 'DSP integrado para plugins UAD'],
    use: ['Producción profesional moderna', 'Estudios con racks analógicos'],
    tracks: [],
    build: [
      '16 canales AD/DA alta resolución',
      'DSP HEXA Core',
      'Soporte Dolby Atmos 9.1.6',
      'Integración con plugins analógicos',
    ],
    price: 'USD $4.250',
  },
  {
    name: 'Apogee Symphony I/O Mk II',
    image: 'https://media.wavescdn.com/images/products/hardware/max/apogee-symphony-mk-ii-sg.png?fit=max&auto=format&ixlib=imgixjs-3.6.1',
    why: ['Referencia absoluta en conversion AD/DA', 'Sonido transparente'],
    use: ['Estudios high-end', 'Grabacion y mastering'],
    tracks: [],
    build: ['Modular y configurable', 'Conversion ultra precisa', 'Latencia muy baja'],
    price: 'USD $8.000',
  },
  {
    name: 'Prism Sound Atlas / Lyra 2',
    image:
      'https://cdn10.bigcommerce.com/s-i0vplte0/products/1488/images/5073/product-hdr-lyra2-front-black-carousel2__79612.1607044491.1280.1280.png?c=2',
    why: ['Nivel mastering', 'Transparencia absoluta'],
    use: ['Estudios de mastering', 'Broadcast'],
    tracks: [],
    build: ['Conversion precisa', 'Bajo jitter', 'Clocking avanzado'],
    price: 'USD $4.500',
  },
  {
    name: 'Antelope Orion 32+ / Galaxy',
    image: 'https://en.antelopeaudio.com/wp-content/uploads/2024/01/A-New-Level-of-Immersion-Orion-32-Gen-4.png',
    why: ['Muchos canales y clocking de alto nivel'],
    use: ['Estudios grandes', 'Tracking masivo'],
    tracks: [],
    build: ['Hasta 32 canales', 'Clocking propietario', 'DSP Synergy Core'],
    price: 'USD $4.500',
  },
  {
    name: 'RME Fireface UFX+ / UFX III',
    image: 'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774032020/RME_Fireface_UFX___UFX_III_2_rrydbk.png',
    why: ['La interfaz mas estable del mercado', 'Fiabilidad absoluta'],
    use: ['Broadcast', 'Directo', 'Grabacion critica'],
    tracks: [],
    build: ['Drivers ultra estables', 'TotalMix FX', 'Baja latencia consistente'],
    price: 'USD $3.250',
  },
]

const drumProducts = [
  {
    name: "DW Collector's Series",
    image: 'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774032048/DW_Collector_s_Series_wdydpe.png',
    why: ['Bateria mas customizable y premium del mercado', 'Estandar en estudios y giras'],
    use: ['Dave Grohl', 'Travis Barker', 'Neil Peart'],
    tracks: [],
    build: [
      'Fabricacion personalizada',
      'True-Pitch tuning',
      'STM mounting',
      'Opciones de madera: maple, birch, hybrid',
    ],
    price: 'USD $7.000',
  },
  {
    name: 'Pearl Masterworks',
    image:
      'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774032059/Pearl_Masterworks_guwlg6.png',
    why: ['Nivel boutique dentro de marca industrial', 'Usada en escenarios y grabaciones'],
    use: ['Dennis Chambers', 'Estudios de alto nivel'],
    tracks: [],
    build: ['Totalmente custom', 'Opciones híbridas: maple, birch, mahogany'],
    price: 'USD $8.500',
  },
  {
    name: 'Yamaha Recording Custom',
    image:
      'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774032067/Yamaha_Recording_Custom_gytgrr.png',
    why: ['Una de las baterías más grabadas', 'Estándar en estudio'],
    use: ['Steve Gadd', 'Vinnie Colaiuta'],
    tracks: [],
    build: ['100% birch shells', 'Sonido seco y controlado'],
    price: 'USD $5.000',
  },
  {
    name: 'Tama Star / Starclassic Maple',
    image: 'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774032050/Tama_Star___Starclassic_Maple_nfmqnu.png',
    why: ['Sonido potente y moderno', 'Muy usada en rock y metal'],
    use: ['Lars Ulrich', 'Simon Phillips'],
    tracks: [],
    build: ['Maple shells', 'Hardware solido', 'Ataque fuerte y definido'],
    price: 'USD $5.000',
  },
  {
    name: 'Gretsch USA Custom',
    image: 'https://res.cloudinary.com/dhgifjpkh/image/upload/v1774032066/Gretsch_USA_Custom_xujlao.png',
    why: ['Sonido clásico de jazz y estudio', 'Identidad sonora única'],
    use: ['Tony Williams', 'Phil Collins'],
    tracks: [],
    build: ['Maple + gumwood shells', 'Sonido calido y vintage'],
    price: 'USD $6.000',
  },
]

const answers = reactive({})
const glow = reactive({ x: 50, y: 40 })
const view = ref('category')
const currentCategory = ref(null)
const currency = ref('CLP')

const currencyRates = {
  USD: 1,
  EUR: 0.92,
  GBP: 0.79,
  JPY: 150,
  MXN: 17,
  CLP: 950,
}

const currencyLabels = {
  USD: 'USD',
  EUR: 'EUR',
  GBP: 'GBP',
  JPY: 'JPY',
  MXN: 'MXN',
  CLP: 'CLP',
}

const imageViewer = reactive({ url: '', name: '', product: null })
const cartItems = reactive([])
const cartDiscounts = reactive([])
const cartBenefits = reactive([])
const cartFlash = ref(false)
const experienceFlash = ref(false)
const menuOpen = ref(false)
const audioEl = ref(null)
const customPack = reactive({ one: '', two: '', three: '' })

const openImage = (product) => {
  if (!product) return
  stopExperienceAudio()
  imageViewer.url = product.image
  imageViewer.name = product.name
  imageViewer.product = product
  playExperienceAudio(product.name)
}

const closeImage = () => {
  stopExperienceAudio()
  imageViewer.url = ''
  imageViewer.name = ''
  imageViewer.product = null
}

const addFromExperience = (product) => {
  stopExperienceAudio()
  addToCart(product)
  experienceFlash.value = true
  setTimeout(() => {
    experienceFlash.value = false
    closeImage()
  }, 350)
}

const scrollToSection = (id) => {
  menuOpen.value = false
  const target = document.getElementById(id)
  if (target) {
    target.scrollIntoView({ behavior: 'smooth', block: 'start' })
  }
}

const contactAdvisor = (subject = '') => {
  const base = 'mailto:asesoria@goldstore.com'
  const query = subject ? `?subject=${encodeURIComponent(subject)}` : ''
  window.location.href = `${base}${query}`
}

const findProductByName = (name) => {
  if (currentCategory.value === 'Guitarras') {
    return (guitarProducts[answers.subType] || []).find((item) => item.name === name)
  }
  if (currentCategory.value === 'Pianos') {
    return (pianoProducts[answers.subType] || []).find((item) => item.name === name)
  }
  if (currentCategory.value === 'Bajos') {
    return (bassProducts[answers.subType] || []).find((item) => item.name === name)
  }
  if (currentCategory.value === 'Micrófonos') {
    return (micProducts[answers.subType] || []).find((item) => item.name === name)
  }
  if (currentCategory.value === 'Interfaces') {
    return interfaceProducts.find((item) => item.name === name)
  }
  if (currentCategory.value === 'Baterías') {
    return drumProducts.find((item) => item.name === name)
  }
  if (currentCategory.value === 'Controladores') {
    return controllerProducts.find((item) => item.name === name)
  }
  return null
}

const parseUsdMin = (price) => {
  if (!price) return 0
  const numbers = String(price)
    .replace(/[^0-9.\-–]/g, '')
    .replace(/\./g, '')
    .split(/[–-]/)
    .map((part) => Number.parseFloat(part))
    .filter((num) => Number.isFinite(num))
  return numbers.length ? numbers[0] : 0
}

const addBenefit = (type, message) => {
  if (cartBenefits.find((entry) => entry.type === type)) return
  cartBenefits.push({ type, message })
}

const addToCart = (product, options = {}) => {
  if (!product) return
  if (!options.skipBenefit) {
    addBenefit(
      'instrument',
      'Por la compra de este instrumento tienes 25% de descuento en convenio con estudios profesionales.'
    )
  }
  const existing = cartItems.find((item) => item.name === product.name)
  if (existing) {
    existing.qty += 1
    cartFlash.value = true
    setTimeout(() => {
      cartFlash.value = false
    }, 800)
    return
  }
  cartItems.push({
    name: product.name,
    image: product.image,
    priceUsd: parseUsdMin(product.price),
    priceLabel: product.price,
    qty: 1,
  })
  cartFlash.value = true
  setTimeout(() => {
    cartFlash.value = false
  }, 800)
}

const addDiscount = (label, amountUsd) => {
  if (!amountUsd || amountUsd <= 0) return
  cartDiscounts.push({ label, amountUsd })
}

const increaseQty = (name) => {
  const item = cartItems.find((entry) => entry.name === name)
  if (item) item.qty += 1
}

const decreaseQty = (name) => {
  const item = cartItems.find((entry) => entry.name === name)
  if (!item) return
  if (item.qty > 1) {
    item.qty -= 1
  } else {
    removeFromCart(name)
  }
}

const removeFromCart = (name) => {
  const index = cartItems.findIndex((entry) => entry.name === name)
  if (index >= 0) cartItems.splice(index, 1)
}

const summaryText = computed(() => {
  const values = [answers.category, answers.subType, answers.product].filter(Boolean)
  if (!values.length) return 'Aun no has seleccionado preferencias.'
  return `${values.join(' · ')} · Selección premium`
})

const primaryCategories = computed(() => categories.filter((item) => !item.extra))
const extraCategories = computed(() => categories.filter((item) => item.extra))

const activeCopy = computed(() => {
  if (view.value === 'category') {
    return {
      question: '¿Qué quieres explorar hoy?',
      description: 'Instrumentos premium, seleccionados sin ruido ni exceso.',
      options: categories,
    }
  }
  if (view.value === 'guitarType') {
    return {
      question: '¿Qué tipo de guitarra buscas?',
      description: 'Elige la familia que define tu sonido.',
      options: guitarTypes,
    }
  }
  if (view.value === 'pianoType') {
    return {
      question: '¿Qué tipo de piano buscas?',
      description: 'Elige la familia que define tu interpretación.',
      options: pianoTypes,
    }
  }
  if (view.value === 'bassType') {
    return {
      question: '¿Qué tipo de bajo buscas?',
      description: 'Elige la familia que define tu base.',
      options: bassTypes,
    }
  }
  if (view.value === 'micType') {
    return {
      question: '¿Qué tipo de micrófono buscas?',
      description: 'Elige la familia que define tu captura.',
      options: micTypes,
    }
  }
  if (view.value === 'packs') {
    return {
      question: 'GOLD PACKS',
      description: 'Soluciones profesionales con instrumentos reales para producción seria.',
      options: goldPacks.map((pack) => ({
        label: pack.name,
        hint: pack.focus,
      })),
    }
  }
  if (view.value === 'studios') {
    return {
      question: 'Convenios de estudios',
      description: 'Beneficios exclusivos por comprar en Gold Store y grabar en estudios legendarios.',
      options: studioDeals.map((studio) => ({
        label: studio.name,
        hint: studio.location,
      })),
    }
  }
  if (view.value === 'products') {
    let list = []
    if (currentCategory.value === 'Guitarras') {
      list = guitarProducts[answers.subType] || []
    }
    if (currentCategory.value === 'Pianos') {
      if (answers.subType === 'Controladores') {
        list = controllerProducts
      } else {
        list = pianoProducts[answers.subType] || []
      }
    }
    if (currentCategory.value === 'Bajos') {
      list = bassProducts[answers.subType] || []
    }
    if (currentCategory.value === 'Micrófonos') {
      list = micProducts[answers.subType] || []
    }
    if (currentCategory.value === 'Interfaces') {
      list = interfaceProducts
    }
    if (currentCategory.value === 'Baterías') {
      list = drumProducts
    }
    return {
      question: 'Modelos premium disponibles',
      description: 'Selecciona el modelo que quieres explorar.',
      options: list.map((item) => ({
        label: item.name,
        hint: 'Disponible para asesoría',
        image: item.image,
        product: item,
      })),
    }
  }
  return {
    question: 'Selección guiada',
    description: 'Estamos preparando esta categoria.',
    options: [],
  }
})

const selectOption = (stepId, label) => {
  if (view.value === 'category') {
    answers.category = label
    currentCategory.value = label
    if (label === 'Guitarras') {
      view.value = 'guitarType'
    } else {
      if (label === 'Pianos') {
        view.value = 'pianoType'
      } else if (label === 'Bajos') {
        view.value = 'bassType'
      } else if (label === 'Micrófonos') {
        view.value = 'micType'
      } else if (label === 'Interfaces') {
        view.value = 'products'
      } else if (label === 'Baterías') {
        view.value = 'products'
      } else if (label === 'GOLD PACKS') {
        view.value = 'packs'
      } else if (label === 'Convenios de estudios') {
        view.value = 'studios'
      } else {
        view.value = 'pending'
      }
    }
    return
  }
  if (view.value === 'guitarType') {
    answers.subType = label
    view.value = 'products'
    return
  }
  if (view.value === 'pianoType') {
    answers.subType = label
    view.value = 'products'
    return
  }
  if (view.value === 'bassType') {
    answers.subType = label
    view.value = 'products'
    return
  }
  if (view.value === 'micType') {
    answers.subType = label
    view.value = 'products'
    return
  }
  if (view.value === 'packs') {
    answers.pack = label
    view.value = 'packDetail'
    return
  }
  if (view.value === 'studios') {
    answers.studio = label
    view.value = 'studioDetail'
    return
  }
  if (view.value === 'products') {
    answers.product = label
    return
  }
  if (view.value === 'pending') {
    restart()
  }
}

const selectedProduct = computed(() => {
  if (view.value !== 'products') return null
  let list = []
  if (currentCategory.value === 'Guitarras') {
    list = guitarProducts[answers.subType] || []
  }
  if (currentCategory.value === 'Pianos') {
    if (answers.subType === 'Controladores') {
      list = controllerProducts
    } else {
      list = pianoProducts[answers.subType] || []
    }
  }
  if (currentCategory.value === 'Bajos') {
    list = bassProducts[answers.subType] || []
  }
  if (currentCategory.value === 'Micrófonos') {
    list = micProducts[answers.subType] || []
  }
  if (currentCategory.value === 'Interfaces') {
    list = interfaceProducts
  }
  if (currentCategory.value === 'Baterías') {
    list = drumProducts
  }
  return list.find((item) => item.name === answers.product) || null
})

const selectedPack = computed(() => {
  if (view.value !== 'packDetail') return null
  return goldPacks.find((pack) => pack.name === answers.pack) || null
})

const selectedStudio = computed(() => {
  if (view.value !== 'studioDetail') return null
  return studioDeals.find((studio) => studio.name === answers.studio) || null
})

const studioCarouselIndex = reactive({})

const getStudioIndex = (name) => {
  if (!name) return 0
  return Number.isFinite(studioCarouselIndex[name]) ? studioCarouselIndex[name] : 0
}

const setStudioIndex = (name, value, length) => {
  if (!name || !length) return
  const next = ((value % length) + length) % length
  studioCarouselIndex[name] = next
}

const nextStudioImage = (studio) => {
  if (!studio?.images?.length) return
  const current = getStudioIndex(studio.name)
  setStudioIndex(studio.name, current + 1, studio.images.length)
}

const prevStudioImage = (studio) => {
  if (!studio?.images?.length) return
  const current = getStudioIndex(studio.name)
  setStudioIndex(studio.name, current - 1, studio.images.length)
}

const packItemMap = {
  'Fender Stratocaster': 'Fender American Professional II Stratocaster',
  'Universal Audio Apollo x16': 'Universal Audio Apollo x16 Gen 2',
  'Telefunken U47': 'Telefunken U47 (Reissue)',
  'Prism Sound Atlas': 'Prism Sound Atlas / Lyra 2',
  'Music Man StingRay': 'Music Man StingRay Special',
  'Tama Starclassic Maple': 'Tama Star / Starclassic Maple',
  'Antelope Orion': 'Antelope Orion 32+ / Galaxy',
  'Steinway Model D': 'Steinway & Sons Model D (D-274)',
  'Telefunken ELA M 251': 'Telefunken ELA M 251E',
  'RME Fireface UFX': 'RME Fireface UFX+ / UFX III',
}

const allProductOptions = computed(() => {
  const list = []
  const pushItems = (items, group) => {
    items.forEach((item) => {
      list.push({ label: item.name, group })
    })
  }
  Object.values(guitarProducts).forEach((items) => pushItems(items, 'Guitarras'))
  Object.values(pianoProducts).forEach((items) => pushItems(items, 'Pianos'))
  pushItems(controllerProducts, 'Controladores')
  Object.values(bassProducts).forEach((items) => pushItems(items, 'Bajos'))
  Object.values(micProducts).forEach((items) => pushItems(items, 'Micrófonos'))
  pushItems(interfaceProducts, 'Interfaces')
  pushItems(drumProducts, 'Baterías')
  return list
})

const findAnyProductByName = (name) => {
  const matchName = packItemMap[name] || name
  const searchGroups = [
    ...Object.values(guitarProducts),
    ...Object.values(pianoProducts),
    controllerProducts,
    ...Object.values(bassProducts),
    ...Object.values(micProducts),
    interfaceProducts,
    drumProducts,
  ]
  for (const group of searchGroups) {
    const found = group.find((item) => item.name === matchName)
    if (found) return found
  }
  return null
}

const addPackToCart = (pack) => {
  if (!pack) return
  const items = [...pack.instruments, pack.mic, pack.interface]
  let subtotal = 0
  items.forEach((name) => {
    const product = findAnyProductByName(name)
    if (product) {
      addToCart(product, { skipBenefit: true })
      subtotal += parseUsdMin(product.price)
    }
  })
  addBenefit(
    'goldpack',
    'Por la compra de tu GOLD PACK obtienes 40% de descuento en estudios profesionales.'
  )
  addDiscount('Descuento GOLD PACK 25%', subtotal * 0.25)
}

const addCustomPackToCart = () => {
  const items = [customPack.one, customPack.two, customPack.three].filter(Boolean)
  let subtotal = 0
  items.forEach((name) => {
    const product = findAnyProductByName(name)
    if (product) {
      addToCart(product, { skipBenefit: true })
      subtotal += parseUsdMin(product.price)
    }
  })
  if (items.length === 3) {
    addBenefit(
      'custompack',
      'Por armar tu GOLD PACK te llevas 35% de descuento en convenio con estudios profesionales.'
    )
    addDiscount('Descuento GOLD PACK Personalizado 15%', subtotal * 0.15)
  }
}

const detailImageClass = computed(() => {
  const name = selectedProduct.value?.name
  return {
    'detail-image--fg9': name === 'Yamaha FG9',
    'detail-image--nylon-wide': name === 'Ramirez 1a' || name === 'Alhambra 11P',
    'detail-image--ramirez': name === 'Ramirez 1a',
    'detail-image--alhambra': name === 'Alhambra 11P',
    'detail-image--gc82': name === 'Yamaha GC82',
    'detail-image--multiac': name === 'Godin Multiac Nylon',
    'detail-image--grand':
      name === 'Bosendorfer 290 Imperial' ||
      name === 'Fazioli F308' ||
      name === 'Yamaha CFX' ||
      name === 'Shigeru Kawai SK-EX' ||
      name === 'Rickenbacker 4003' ||
      name === 'Tacoma Thunderchief (CB10 / CB105)' ||
      name === 'Martin BC-16E' ||
      name === 'Ibanez AEB10 / AEB Series' ||
      name === 'Godin A4 Ultra (Semi-acustico)' ||
      name === "DW Collector's Series" ||
      name === 'Pearl Masterworks' ||
      name === 'Yamaha Recording Custom' ||
      name === 'Tama Star / Starclassic Maple' ||
      name === 'Gretsch USA Custom' ||
      name === 'Neumann U87 Ai' ||
      name === 'Sony C-800G' ||
      name === 'Telefunken U47 (Reissue)' ||
      name === 'Telefunken ELA M 251E' ||
      name === 'AKG C414 XLII' ||
      name === 'Shure SM7B' ||
      name === 'Electro-Voice RE20' ||
      name === 'Neumann TLM 103' ||
      name === 'Shure SM58' ||
      name === 'Universal Audio Sphere DLX' ||
      name === 'Universal Audio Apollo x16 Gen 2' ||
      name === 'Apogee Symphony I/O Mk II' ||
      name === 'Prism Sound Atlas / Lyra 2' ||
      name === 'Antelope Orion 32+ / Galaxy' ||
      name === 'RME Fireface UFX+ / UFX III',
    'detail-image--stage':
      name === 'Yamaha CP88' ||
      name === 'Roland RD-2000' ||
      name === 'Kawai MP11SE' ||
      name === 'Dexibell VIVO S10' ||
      name === 'Novation SL MkIII',
  }
})

const videoByProduct = {
  'Fender American Professional II Stratocaster': 'https://www.youtube.com/watch?v=LTseTg48568',
  'Gibson Les Paul Standard': 'https://www.youtube.com/watch?v=1w7OgIMMRc4',
  'PRS Custom 24': 'https://www.youtube.com/watch?v=6Whgn_iE5uc',
  'Ibanez JEM7V': 'https://www.youtube.com/watch?v=e0AjQUI5NN4',
  'Ernie Ball Music Man Majesty (John Petrucci)': 'https://www.youtube.com/watch?v=mipc-JxrhRk',
  'Gibson ES-335': 'https://www.youtube.com/watch?v=SgXSomPE_FY',
  'Gibson ES-175': 'https://www.youtube.com/watch?v=X00zEK4AKO4',
  'Gretsch White Falcon': 'https://www.youtube.com/watch?v=zk_WpqVFYZg',
  'PRS Hollowbody II': 'https://www.youtube.com/watch?v=_DfQC5qHhbo',
  'Ibanez GB10': 'https://www.youtube.com/watch?v=kVc5rCl0BIs',
  'Taylor 814ce': 'https://www.youtube.com/watch?v=r0yq_yXFQhg',
  'Martin D-28': 'https://www.youtube.com/watch?v=vWwgrjjIMXA',
  'Gibson J-45': 'https://www.youtube.com/watch?v=Ve-mANenpC4',
  'Yamaha FG9': 'https://www.youtube.com/watch?v=lp-EO5I60KA',
  'Taylor K24ce': 'https://www.youtube.com/watch?v=8mCCMhuKEYw',
  'Ramirez 1a': 'https://www.youtube.com/watch?v=IrPE3YQ8xx4',
  'Yamaha GC82': 'https://www.youtube.com/watch?v=8PzuwGSjYxU',
  'Cordoba Master Series': 'https://www.youtube.com/watch?v=l-qgum7hFXk',
  'Alhambra 11P': 'https://www.youtube.com/watch?v=MO4s9INrdas',
  'Godin Multiac Nylon': 'https://www.youtube.com/watch?v=tsmThCBkBUo',
  'Steinway & Sons Model D (D-274)': 'https://www.youtube.com/watch?v=o_xKvmu79qE',
  'Bosendorfer 290 Imperial': 'https://www.youtube.com/watch?v=0H21wHkKNag',
  'Fazioli F308': 'https://www.youtube.com/watch?v=G3in_Ewqu_g',
  'Yamaha CFX': 'https://www.youtube.com/watch?v=DtnljX1bjRs',
  'Shigeru Kawai SK-EX': 'https://www.youtube.com/watch?v=WCqlYvjv8x4',
  'Yamaha CP88': 'https://www.youtube.com/watch?v=R7yHYe9sbjo',
  'Nord Stage 4': 'https://www.youtube.com/watch?v=L_XJ_s5IsQc',
  'Roland RD-2000': 'https://www.youtube.com/watch?v=mBCNLzhHYYo',
  'Kawai MP11SE': 'https://www.youtube.com/watch?v=2YcwbMGLjhA',
  'Dexibell VIVO S10': 'https://www.youtube.com/watch?v=fKFFuZlrpiY',
  'Native Instruments Komplete Kontrol S88 MK2': 'https://www.youtube.com/watch?v=5frqnSj702c',
  'Arturia KeyLab 88 MkII': 'https://www.youtube.com/watch?v=w-dTrdxJGyQ',
  'Akai MPK261': 'https://www.youtube.com/watch?v=ZOKkWDsJKVY',
  'Novation SL MkIII': 'https://www.youtube.com/watch?v=oJAT3PutkGI',
  'M-Audio Hammer 88 Pro': 'https://www.youtube.com/watch?v=sK0pcoX4FRk',
  'Fender Precision Bass (American / Custom Shop)': 'https://www.youtube.com/watch?v=y2bVIBwpCTA',
  'Music Man StingRay Special': 'https://www.youtube.com/watch?v=-hWzduNqlmA',
  'Fender Jazz Bass': 'https://www.youtube.com/watch?v=M7zspGRqsyM',
  'Rickenbacker 4003': 'https://www.youtube.com/watch?v=yYvkICbTZIQ',
  'Fodera Emperor (Custom)': 'https://www.youtube.com/watch?v=PA-ZKDOoBnk',
  'Tacoma Thunderchief (CB10 / CB105)': 'https://www.youtube.com/watch?v=CkAgrtuTDTs',
  'Taylor GS Mini Bass': 'https://www.youtube.com/watch?v=KRX-5jhtvn0',
  'Martin BC-16E': 'https://www.youtube.com/watch?v=8pGyFGmXqkE',
  'Ibanez AEB10 / AEB Series': 'https://www.youtube.com/watch?v=EXNbdtN-P2M',
  'Godin A4 Ultra (Semi-acustico)': 'https://www.youtube.com/watch?v=YoHWGzmeIHc',
  'Neumann U87 Ai': 'https://www.youtube.com/watch?v=sOnqjkJTMaA',
  'Sony C-800G': 'https://www.youtube.com/watch?v=SWMo949JpJk',
  'Telefunken U47 (Reissue)': 'https://www.youtube.com/watch?v=JYuyWrkwpok',
  'Telefunken ELA M 251E': 'https://www.youtube.com/watch?v=9bFHsd3o1w0',
  'AKG C414 XLII': 'https://www.youtube.com/watch?v=YlUKcNNmywk',
  'Shure SM7B': 'https://www.youtube.com/watch?v=Zi_XLOBDo_Y',
  'Electro-Voice RE20': 'https://www.youtube.com/watch?v=zNWRL5Az8-M',
  'Neumann TLM 103': 'https://www.youtube.com/watch?v=Nffp3Fyjveg',
  'Shure SM58': 'https://www.youtube.com/watch?v=frdBb9Slu1A',
  'Universal Audio Sphere DLX': 'https://www.youtube.com/watch?v=n6ErKaUi36M',
  'Universal Audio Apollo x16 Gen 2': 'https://www.youtube.com/watch?v=mvwkzAq40Bw',
  'Apogee Symphony I/O Mk II': 'https://www.youtube.com/watch?v=zi5kDkSexGA',
  'Prism Sound Atlas / Lyra 2': 'https://www.youtube.com/watch?v=3sOFuN38YM8',
  'Antelope Orion 32+ / Galaxy': 'https://www.youtube.com/watch?v=4bTHYGPrnZQ',
  'RME Fireface UFX+ / UFX III': 'https://www.youtube.com/watch?v=LZrnDHmPmpU',
  "DW Collector's Series": 'https://www.youtube.com/watch?v=eBG7P-K-r1Y',
  'Pearl Masterworks': 'https://www.youtube.com/watch?v=pel0k2-uhpE',
  'Yamaha Recording Custom': 'https://www.youtube.com/watch?v=Py0FdS-e960',
  'Tama Star / Starclassic Maple': 'https://www.youtube.com/watch?v=XgNXw-EkMw4',
  'Gretsch USA Custom': 'https://www.youtube.com/watch?v=YkADj0TPrJA',
}

const getEmbedUrl = (url) => {
  if (!url) return ''
  try {
    const parsed = new URL(url)
    if (parsed.hostname.includes('youtu.be')) {
      return `https://www.youtube.com/embed/${parsed.pathname.replace('/', '')}`
    }
    const id = parsed.searchParams.get('v')
    return id ? `https://www.youtube.com/embed/${id}` : ''
  } catch (error) {
    return ''
  }
}

const experienceVideoUrl = computed(() => {
  const name = imageViewer.product?.name
  return getEmbedUrl(videoByProduct[name])
})

const audioByProduct = {
  'PRS Custom 24': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044565/PRS_Custom_24_bj0jok.mp3',
  'Akai MPK261': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044559/Akai_MPK261_hqidev.mp3',
  'Yamaha CP88': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044558/Yamaha_CP88_ag9xvz.mp3',
  'Ernie Ball Music Man Majesty (John Petrucci)': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044553/Music_Man_Majesty_John_Petrucci_xozfxc.mp3',
  'Taylor 814ce': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044551/Taylor_814ce_nqhshg.mp3',
  'Telefunken U47 (Reissue)': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044546/Telefunken_U47_sotx6h.mp3',
  'Gretsch White Falcon': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044544/Gretsch_White_Falcon_hnmosc.mp3',
  'Ibanez JEM7V': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044538/Ibanez_JEM7V_k24hhp.mp3',
  'Ibanez AEB10 / AEB Series': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044537/Ibanez_AEB_Series_z6gwvm.mp3',
  'Fender American Professional II Stratocaster': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044533/Fender_American_Professional_II_Stratocaster_ct71kl.mp3',
  'Fazioli F308': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044531/Fazioli_F308_xu0ubv.mp3',
  'Martin D-28': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044527/Martin_D-28_higay8.mp3',
  'Native Instruments Komplete Kontrol S88 MK2': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044525/Native_Instruments_Komplete_Kontrol_S88_MK2_inoi5c.mp3',
  'Yamaha CFX': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044520/Yamaha_CFX_ur27ap.mp3',
  'Pearl Masterworks': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044519/Pearl_Masterworks_j64v3c.mp3',
  'Gibson Les Paul Standard': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044514/Gibson_Les_Paul_Standard_zgs4jj.mp3',
  "DW Collector's Series": 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044512/DW_Collector_s_Series_qrahp2.mp3',
  'Yamaha Recording Custom': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044505/Yamaha_Recording_Custom_fobnis.mp3',
  'Roland RD-2000': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044503/Roland_RD-2000_chxhf0.mp3',
  'Tama Star / Starclassic Maple': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044500/Tama_Star_Starclassic_Maple_lzrodt.mp3',
  'Kawai MP11SE': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044493/Kawai_MP11SE_p2ygq3.mp3',
  'Steinway & Sons Model D (D-274)': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044494/Steinway_Model_D_uwaugp.mp3',
  'Gretsch USA Custom': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044488/Gretsch_USA_Custom_ifgfmk.mp3',
  'Shigeru Kawai SK-EX': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044485/Shigeru_Kawai_SK-EX_zwsq6q.mp3',
  'Nord Stage 4': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044483/Nord_Stage_4_cc73z1.mp3',
  'Taylor K24ce': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044478/Taylor_K24ce_ohqauv.mp3',
  'PRS Hollowbody II': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044477/PRS_Hollowbody_II_zxzcwo.mp3',
  'Gibson ES-175': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044474/Gibson_ES-175_axglta.mp3',
  'Tacoma Thunderchief (CB10 / CB105)': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044471/Tacoma_Thunderchief_fhoeth.mp3',
  'Shure SM7B': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044466/Shure_SM7B_sertwe.mp3',
  'Fender Precision Bass (American / Custom Shop)': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044464/Fender_Precision_Bass_zmikke.mp3',
  'Arturia KeyLab 88 MkII': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044460/Arturia_KeyLab_88_MkII_rkzqwd.mp3',
  'Gibson ES-335': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044459/Gibson_ES-335_frk18c.mp3',
  'Fodera Emperor (Custom)': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044454/Fodera_Emperor_rxvebz.mp3',
  'Sony C-800G': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044453/Sony_C-800G_qtwx22.mp3',
  'Neumann U87 Ai': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044449/Neumann_U87_Ai_uvrjym.mp3',
  'Rickenbacker 4003': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044447/Rickenbacker_4003_bq0car.mp3',
  'Novation SL MkIII': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044443/Novation_SL_MkIII_lcvnri.mp3',
  'Godin A4 Ultra (Semi-acustico)': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044441/Godin_A4_Ultra_tj9tuw.mp3',
  'Yamaha FG9': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044438/Yamaha_FG9_xwilqj.mp3',
  'Music Man StingRay Special': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044436/Music_Man_StingRay_Special_csp33s.mp3',
  'Dexibell VIVO S10': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044432/Dexibell_VIVO_S10_qq4cb7.mp3',
  'Yamaha GC82': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044431/Yamaha_GC82_ivit06.mp3',
  'Taylor GS Mini Bass': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044426/Taylor_GS_Mini_Bass_jssrt7.mp3',
  'Universal Audio Apollo x16 Gen 2': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044424/Universal_Audio_Apollo_x16_ufdsmd.mp3',
  'Godin Multiac Nylon': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044421/Godin_Multiac_Nylon_qb5to1.mp3',
  'Gibson J-45': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044419/Gibson_J-45_louzzv.mp3',
  'Ibanez GB10': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044412/Ibanez_GB10_yvba7x.mp3',
  'M-Audio Hammer 88 Pro': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044410/M-Audio_Hammer_88_Pro_ef64c7.mp3',
  'Ramirez 1a': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044404/Rami%CC%81rez_1a_zyzyby.mp3',
  'AKG C414 XLII': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774044403/AKG_C414_XLII_whzaox.mp3',
  'Telefunken ELA M 251E': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774043674/Telefunken_ELA_M_251E_d5fahu.mp3',
  'Apogee Symphony I/O Mk II': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774043670/Apogee_Symphony_I_O_Mk_II_e1ks7u.mp3',
  'Bosendorfer 290 Imperial': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774043668/Bo%CC%88sendorfer_290_Imperial_ig9x1k.mp3',
  'Electro-Voice RE20': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774043664/Electro-Voice_RE20_soae5k.mp3',
  'Martin BC-16E': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774043663/Martin_BC-16E_g6kksd.mp3',
  'Shure SM58': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774043660/Shure_SM58_emzx7o.mp3',
  'Fender Jazz Bass': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774043658/Fender_Jazz_Bass_vcoemb.mp3',
  'Universal Audio Sphere DLX': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774043655/Universal_Audio_Sphere_DLX_pvsmq3.mp3',
  'Prism Sound Atlas / Lyra 2': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774043653/Prism_Sound_Atlas_x87afv.mp3',
  'Cordoba Master Series': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774043650/Co%CC%81rdoba_Master_Series_m527zj.mp3',
  'RME Fireface UFX+ / UFX III': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774043648/RME_Fireface_UFX_fm2vpo.mp3',
  'Alhambra 11P': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774043645/Alhambra_11P_bcwbkc.mp3',
  'Neumann TLM 103': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774043645/Neumann_TLM_103_s9t9hi.mp3',
  'Antelope Orion 32+ / Galaxy': 'https://res.cloudinary.com/dhgifjpkh/video/upload/v1774043644/Antelope_Orion_ocldz9.mp3',
}

const playExperienceAudio = async (name) => {
  const src = audioByProduct[name]
  if (!audioEl.value || !src) return
  audioEl.value.src = src
  audioEl.value.currentTime = 0
  try {
    await audioEl.value.play()
  } catch (error) {
    // Autoplay can be blocked; ignore silently.
  }
}

const stopExperienceAudio = () => {
  if (!audioEl.value) return
  audioEl.value.pause()
  audioEl.value.currentTime = 0
  audioEl.value.src = ''
}


const cartSubtotalUsd = computed(() => {
  return cartItems.reduce((sum, item) => sum + item.priceUsd * item.qty, 0)
})

const cartDiscountUsd = computed(() => {
  return cartDiscounts.reduce((sum, discount) => sum + discount.amountUsd, 0)
})

const cartTotalUsd = computed(() => {
  return Math.max(0, cartSubtotalUsd.value - cartDiscountUsd.value)
})

const cartTotalConverted = computed(() => {
  const rate = currencyRates[currency.value] || 1
  return cartTotalUsd.value * rate
})

const cartSubtotalConverted = computed(() => {
  const rate = currencyRates[currency.value] || 1
  return cartSubtotalUsd.value * rate
})

const cartDiscountConverted = computed(() => {
  const rate = currencyRates[currency.value] || 1
  return cartDiscountUsd.value * rate
})

const parsedPriceRange = computed(() => {
  if (!selectedProduct.value?.price) return null
  const numbers = String(selectedProduct.value.price)
    .replace(/[^0-9.\-–]/g, '')
    .replace(/\./g, '')
    .split(/[–-]/)
    .map((part) => Number.parseFloat(part))
    .filter((num) => Number.isFinite(num))
  if (!numbers.length) return null
  if (numbers.length === 1) {
    return { min: numbers[0], max: numbers[0] }
  }
  return { min: numbers[0], max: numbers[1] }
})

const convertedPriceRange = computed(() => {
  if (!parsedPriceRange.value) return null
  const rate = currencyRates[currency.value] || 1
  return {
    min: parsedPriceRange.value.min * rate,
    max: parsedPriceRange.value.max * rate,
  }
})

const formatCurrency = (value) => {
  const code = currency.value
  return new Intl.NumberFormat('es-CL', {
    style: 'currency',
    currency: code,
    maximumFractionDigits: code === 'JPY' ? 0 : 2,
  }).format(value)
}

const goBack = () => {
  if (view.value === 'packDetail') {
    view.value = 'packs'
    answers.pack = null
    return
  }
  if (view.value === 'packs') {
    view.value = 'category'
    return
  }
  if (view.value === 'studios') {
    view.value = 'category'
    return
  }
  if (view.value === 'studioDetail') {
    view.value = 'studios'
    answers.studio = null
    return
  }
  if (view.value === 'products') {
    if (currentCategory.value === 'Guitarras') {
      view.value = 'guitarType'
      return
    }
    if (currentCategory.value === 'Pianos') {
      view.value = 'pianoType'
      return
    }
    if (currentCategory.value === 'Bajos') {
      view.value = 'bassType'
      return
    }
    if (currentCategory.value === 'Micrófonos') {
      view.value = 'micType'
      return
    }
    if (currentCategory.value === 'Interfaces') {
      view.value = 'category'
      return
    }
    if (currentCategory.value === 'Baterías') {
      view.value = 'category'
      return
    }
    view.value = 'category'
    return
  }
  if (
    view.value === 'guitarType' ||
    view.value === 'pianoType' ||
    view.value === 'bassType' ||
    view.value === 'micType'
  ) {
    view.value = 'category'
  }
}

const restart = () => {
  view.value = 'category'
  currentCategory.value = null
  Object.keys(answers).forEach((key) => {
    delete answers[key]
  })
}

const handleMove = (event) => {
  const rect = event.currentTarget.getBoundingClientRect()
  glow.x = ((event.clientX - rect.left) / rect.width) * 100
  glow.y = ((event.clientY - rect.top) / rect.height) * 100
}

const handleLeave = () => {
  glow.x = 50
  glow.y = 40
}

</script>

<template>
  <div class="page" id="inicio">
    <div class="ambient" aria-hidden="true"></div>
    <main
      v-show="!imageViewer.url"
      class="card"
      :style="{ '--glow-x': `${glow.x}%`, '--glow-y': `${glow.y}%` }"
      @mousemove="handleMove"
      @mouseleave="handleLeave"
    >
      <header class="brand">
        <div class="logo-wrap">
          <img
            class="logo"
            src="https://res.cloudinary.com/dhgifjpkh/image/upload/v1773961047/Disen%CC%83o_sin_ti%CC%81tulo_2_xi8cel.png"
            alt="Gold Store"
          />
        </div>
        <div class="currency-select">
          <label>
            <span>Moneda</span>
            <select v-model="currency">
              <option v-for="code in Object.keys(currencyLabels)" :key="code" :value="code">
                {{ currencyLabels[code] }}
              </option>
            </select>
          </label>
        </div>
        <div class="brand-text">
          <span class="brand-name">GOLD STORE</span>
          <span class="brand-tag">Instrumentos premium, solo lo mejor.</span>
        </div>
        <div class="brand-spacer" aria-hidden="true"></div>
      </header>

      <div class="panel-actions">
        <button class="ghost gold-action" type="button" @click="restart">Inicio</button>
        <button class="ghost gold-action" type="button" :disabled="view === 'category'" @click="goBack">
          Atrás
        </button>
        <button class="ghost gold-action" type="button" @click="restart">Reiniciar</button>
        <div class="menu">
          <button class="ghost gold-action menu-toggle" type="button" @click="menuOpen = !menuOpen">
            <span class="menu-icon" aria-hidden="true"></span>
            Menú
          </button>
          <div v-if="menuOpen" class="menu-dropdown">
            <button class="menu-item" type="button" @click="scrollToSection('inicio')">Inicio</button>
            <button class="menu-item" type="button" @click="scrollToSection('seleccion')">Selección</button>
            <button class="menu-item" type="button" @click="scrollToSection('producto')">Producto</button>
            <button class="menu-item" type="button" @click="scrollToSection('carrito')">Carrito</button>
          </div>
        </div>
        <button class="ghost gold-action cart-button" type="button" @click="scrollToSection('carrito')">
          <svg viewBox="0 0 24 24" aria-hidden="true">
            <path
              d="M6 6h15l-2 9H8L6 6zm0 0H4m6 14a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0zm9 0a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0z"
              fill="none"
              stroke="currentColor"
              stroke-width="1.5"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
          <span class="cart-count">{{ cartItems.length }}</span>
        </button>
      </div>


      <section class="hero" id="inicio-hero">
        <p class="eyebrow">Curaduría premium</p>
        <h1>Instrumentos premium listos para estudio y escenario.</h1>
        <p class="sub">
          Selección curada, asesoría experta y beneficios exclusivos para artistas que no aceptan compromisos.
        </p>
        <div class="hero-actions">
          <button class="cta" type="button" @click="scrollToSection('seleccion')">Explorar selección</button>
          <button
            class="ghost hero-ghost"
            type="button"
            @click="contactAdvisor()"
          >
            Hablar con un asesor
          </button>
        </div>
        <div class="trust-badges">
          <div class="trust-badge">
            <span>Garantía premium</span>
            <small>Cobertura completa y soporte inmediato</small>
          </div>
          <div class="trust-badge">
            <span>Envíos asegurados</span>
            <small>Logística premium internacional</small>
          </div>
          <div class="trust-badge">
            <span>Asesoría 1:1</span>
            <small>Equipo experto para tu sonido</small>
          </div>
        </div>
      </section>

      <section class="prompt" id="seleccion">
        <p class="eyebrow">Selección guiada</p>
        <h1>{{ activeCopy.question }}</h1>
        <p class="sub">{{ activeCopy.description }}</p>
      </section>

      <section class="options" v-if="view === 'category'">
        <div class="options-group">
          <div class="gold-orbit" :style="{ '--count': primaryCategories.length }">
            <button
              v-for="(option, index) in primaryCategories"
              :key="option.label"
              class="gold-bar-option"
              type="button"
              :style="{ '--i': index }"
              @click="selectOption('flow', option.label)"
            >
              <span class="bar-face"></span>
              <span class="bar-label">{{ option.label }}</span>
              <span class="bar-hint">{{ option.hint }}</span>
            </button>
          </div>
        </div>
        <div class="options-group options-group-extra">
          <p class="options-title">Opciones adicionales</p>
          <div class="gold-orbit" :style="{ '--count': extraCategories.length }">
            <button
              v-for="(option, index) in extraCategories"
              :key="option.label"
              class="gold-bar-option gold-bar-option--extra"
              type="button"
              :style="{ '--i': index }"
              @click="selectOption('flow', option.label)"
            >
              <span class="bar-face"></span>
              <span class="bar-label">{{ option.label }}</span>
              <span class="bar-hint">{{ option.hint }}</span>
            </button>
          </div>
        </div>
      </section>
      <section class="options" v-else-if="activeCopy.options.length">
        <div class="gold-orbit" :style="{ '--count': activeCopy.options.length }">
            <button
              v-for="(option, index) in activeCopy.options"
              :key="option.label"
              class="gold-bar-option"
              type="button"
              :style="{ '--i': index }"
              @click="selectOption('flow', option.label)"
            >
              <span class="bar-face"></span>
              <span class="bar-label">{{ option.label }}</span>
              <span class="bar-hint">{{ option.hint }}</span>
            </button>
        </div>
      </section>

      <section v-if="view === 'packs'" class="pack-builder">
        <h2>Arma tu GOLD PACK</h2>
        <p>Selecciona 3 productos para una solución personalizada.</p>
        <p class="pack-offer">
          <span class="offer-icon" aria-hidden="true">%</span>
          15% de descuento al armar tu GOLD PACK propio
        </p>
        <div class="pack-builder-grid">
          <label>
            <span>Producto 1</span>
            <select v-model="customPack.one">
              <option value="">Selecciona un producto</option>
              <option v-for="item in allProductOptions" :key="`one-${item.label}`" :value="item.label">
                {{ item.label }} · {{ item.group }}
              </option>
            </select>
          </label>
          <label>
            <span>Producto 2</span>
            <select v-model="customPack.two">
              <option value="">Selecciona un producto</option>
              <option v-for="item in allProductOptions" :key="`two-${item.label}`" :value="item.label">
                {{ item.label }} · {{ item.group }}
              </option>
            </select>
          </label>
          <label>
            <span>Producto 3</span>
            <select v-model="customPack.three">
              <option value="">Selecciona un producto</option>
              <option v-for="item in allProductOptions" :key="`three-${item.label}`" :value="item.label">
                {{ item.label }} · {{ item.group }}
              </option>
            </select>
          </label>
        </div>
        <div class="pack-builder-summary">
          <span>Tu GOLD PACK</span>
          <p>{{ [customPack.one, customPack.two, customPack.three].filter(Boolean).join(' · ') || 'Selecciona tus 3 productos' }}</p>
        </div>
        <button
          class="detail-add"
          type="button"
          :disabled="[customPack.one, customPack.two, customPack.three].filter(Boolean).length < 3"
          @click="addCustomPackToCart"
        >
          Agregar GOLD PACK al carrito
        </button>
      </section>
      <section v-if="selectedProduct" class="detail" id="producto">
        <h2 class="detail-title">{{ selectedProduct.name }}</h2>
        <div v-if="selectedProduct.image" class="detail-hero">
          <img
            class="detail-image"
            :class="detailImageClass"
            :src="selectedProduct.image"
            :alt="selectedProduct.name"
            loading="lazy"
            decoding="async"
            @click="openImage(selectedProduct)"
          />
          <button class="detail-zoom" type="button" @click="openImage(selectedProduct)">
            Experiencia en grande
          </button>
        </div>
        <button class="detail-add" type="button" @click="addToCart(selectedProduct)">
          Agregar al carrito
        </button>
      </section>

      <section v-if="selectedPack" class="pack-detail" id="producto">
        <h2 class="pack-title">{{ selectedPack.name }}</h2>
        <p class="pack-focus">{{ selectedPack.focus }}</p>
        <p class="pack-offer">
          <span class="offer-icon" aria-hidden="true">%</span>
          Oferta: 25% de descuento al elegir este GOLD PACK
        </p>
        <div class="pack-grid">
          <div class="pack-block">
            <span class="pack-label">Instrumentos</span>
            <ul>
              <li v-for="item in selectedPack.instruments" :key="item">{{ item }}</li>
            </ul>
          </div>
          <div class="pack-block">
            <span class="pack-label">Micrófono</span>
            <p>{{ selectedPack.mic }}</p>
          </div>
          <div class="pack-block">
            <span class="pack-label">Interfaz</span>
            <p>{{ selectedPack.interface }}</p>
          </div>
        </div>
        <p class="pack-narrative">{{ selectedPack.narrative }}</p>
        <p class="pack-hook">{{ selectedPack.hook }}</p>
        <button class="detail-add" type="button" @click="addPackToCart(selectedPack)">
          Agregar GOLD PACK al carrito
        </button>
      </section>

      <section v-if="selectedStudio" class="studio-detail" id="producto">
        <h2 class="studio-title">{{ selectedStudio.name }}</h2>
        <p class="studio-location">{{ selectedStudio.location }}</p>
        <div v-if="selectedStudio.images?.length" class="studio-carousel">
          <button class="ghost gold-action" type="button" @click="prevStudioImage(selectedStudio)">
            Anterior
          </button>
          <div class="studio-carousel-frame">
            <img
              :src="selectedStudio.images[getStudioIndex(selectedStudio.name)]"
              :alt="`${selectedStudio.name} ${getStudioIndex(selectedStudio.name) + 1}`"
              loading="lazy"
              decoding="async"
            />
          </div>
          <button class="ghost gold-action" type="button" @click="nextStudioImage(selectedStudio)">
            Siguiente
          </button>
        </div>
        <div class="studio-grid">
          <div class="studio-block">
            <span class="studio-label">Por qué está en la cima</span>
            <ul>
              <li v-for="item in selectedStudio.why" :key="item">{{ item }}</li>
            </ul>
          </div>
          <div class="studio-block">
            <span class="studio-label">Producciones</span>
            <ul>
              <li v-for="item in selectedStudio.productions" :key="item">{{ item }}</li>
            </ul>
          </div>
          <div class="studio-block">
            <span class="studio-label">Clave técnica</span>
            <ul>
              <li v-for="item in selectedStudio.technical" :key="item">{{ item }}</li>
            </ul>
          </div>
        </div>
        <div class="studio-discounts">
          <span>Descuentos disponibles</span>
          <p>25% por compra de instrumentos o productos individuales</p>
          <p>40% al comprar un GOLD PACK</p>
          <p>35% por armar tu GOLD PACK</p>
        </div>
        <p v-if="selectedStudio.claim" class="studio-claim">{{ selectedStudio.claim }}</p>
      </section>



      <section class="cart" id="carrito" :class="{ 'is-flash': cartFlash }">
        <div class="cart-header">
          <span class="cart-label">Carrito</span>
           <span class="cart-note">{{ cartItems.length ? `${cartItems.length} productos` : 'Vacío' }}</span>
        </div>
        <div v-if="!cartItems.length" class="cart-empty">
          Agrega productos premium para iniciar tu compra.
        </div>
        <div v-else class="cart-list">
          <div v-for="item in cartItems" :key="item.name" class="cart-item">
            <img
              v-if="item.image"
              :src="item.image"
              :alt="item.name"
              class="cart-image"
              loading="lazy"
              decoding="async"
            />
            <div class="cart-info">
              <span class="cart-name">{{ item.name }}</span>
              <span class="cart-price">{{ item.priceLabel }}</span>
            </div>
            <div class="cart-qty">
              <button type="button" @click="decreaseQty(item.name)">-</button>
              <span>{{ item.qty }}</span>
              <button type="button" @click="increaseQty(item.name)">+</button>
            </div>
            <button class="cart-remove" type="button" @click="removeFromCart(item.name)">Eliminar</button>
          </div>
        </div>
        <div v-if="cartItems.length" class="cart-total">
          <div class="cart-total-left">
            <span class="cart-total-label">Total</span>
            <span class="cart-total-converted">Antes del descuento: {{ formatCurrency(cartSubtotalConverted) }}</span>
            <span v-if="cartDiscountUsd" class="cart-total-discount">
              Descuento: -{{ formatCurrency(cartDiscountConverted) }}
            </span>
            <span class="cart-total-converted cart-total-final">Total: {{ formatCurrency(cartTotalConverted) }}</span>
          </div>
          <div class="cart-total-right">
            <label>
              <span>Moneda</span>
              <select v-model="currency">
                <option v-for="code in Object.keys(currencyLabels)" :key="code" :value="code">
                  {{ currencyLabels[code] }}
                </option>
              </select>
            </label>
          </div>
        </div>
        <div v-if="cartBenefits.length" class="cart-benefits">
          <p v-for="benefit in cartBenefits" :key="benefit.type">{{ benefit.message }}</p>
        </div>
        <div v-if="cartItems.length" class="cart-actions">
          <button class="cta" type="button" @click="contactAdvisor('Quiero cotizar mi selección')">
            Solicitar cotización
          </button>
          <button
            class="ghost gold-action"
            type="button"
            @click="contactAdvisor('Quiero asesoría personalizada')"
          >
            Hablar con asesoría
          </button>
          <p class="cart-actions-note">
            Te respondemos con disponibilidad, tiempos de entrega y opciones de pago.
          </p>
        </div>
      </section>

      <section class="premium-footer">
        <div>
          <span class="premium-label">Contacto</span>
          <p>contacto@goldstore.cl</p>
          <p>+56 9 4827 1935</p>
        </div>
        <div>
          <span class="premium-label">Redes</span>
          <p>Instagram: @goldstore.cl</p>
          <p>YouTube: Gold Store Sessions</p>
        </div>
        <div>
          <span class="premium-label">Boutique</span>
          <p>Santiago, Chile</p>
          <p>Atención: Lun-Sab 10:00-20:00</p>
        </div>
      </section>

      <footer class="card-footer">
        <div class="progress">
          <span class="progress-count">{{ view.toUpperCase() }}</span>
          <span class="progress-text">Ruta premium</span>
        </div>
      </footer>
    </main>

    <div class="sticky-cta" v-if="!imageViewer.url">
      <button class="cta" type="button" @click="scrollToSection('seleccion')">Explorar selección</button>
      <button
        class="ghost hero-ghost"
        type="button"
        @click="contactAdvisor()"
      >
        Hablar con un asesor
      </button>
    </div>

    <div v-if="imageViewer.url" class="experience" :class="{ 'is-flash': experienceFlash }">
      <div class="experience-frame">
        <div class="experience-wall experience-left" v-if="imageViewer.product?.build?.length">
          <span class="experience-label">Construcción</span>
          <ul>
            <li v-for="item in imageViewer.product.build" :key="item">{{ item }}</li>
          </ul>
        </div>

        <div class="experience-center">
          <p class="experience-title">{{ imageViewer.name }}</p>
          <div class="experience-video" v-if="experienceVideoUrl">
            <iframe
              :src="experienceVideoUrl"
              title="Video musical"
              frameborder="0"
              allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
              allowfullscreen
            ></iframe>
          </div>
          <img
            class="experience-image"
            :class="{ 'experience-image--rotate': imageViewer.product?.name === 'Alhambra 11P' }"
            :src="imageViewer.url"
            :alt="imageViewer.name"
            loading="lazy"
            decoding="async"
          />
          <div class="experience-price">
            <span>Valor</span>
            <strong>{{ imageViewer.product?.price }}</strong>
            <span v-if="convertedPriceRange">
              {{ formatCurrency(convertedPriceRange.min) }}
              <em v-if="convertedPriceRange.max !== convertedPriceRange.min">
                – {{ formatCurrency(convertedPriceRange.max) }}
              </em>
            </span>
          </div>
          <div class="experience-actions">
            <button class="ghost gold-action" type="button" @click="closeImage">Volver</button>
            <button class="cta" type="button" @click="addFromExperience(imageViewer.product)">
              Agregar al carrito
            </button>
          </div>
        </div>

        <div class="experience-wall experience-right" v-if="imageViewer.product?.why?.length">
          <span class="experience-label">Por qué es top</span>
          <ul>
            <li v-for="item in imageViewer.product.why" :key="item">{{ item }}</li>
          </ul>
        </div>
      </div>
    </div>

    <audio ref="audioEl" preload="auto"></audio>
  </div>
</template>
