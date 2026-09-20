// App.jsx
import React, { useState, useEffect } from 'react';
import { Lock, Plus, Minus, Search, CheckCircle, MapPin, ChevronRight, Menu, X, ShoppingBag, BarChart, List, RefreshCw } from 'lucide-react';

const App = () => {
  // --- ÉTATS GLOBAUX ---
  const [isAdmin, setIsAdmin] = useState(false);
  const [showAdminLogin, setShowAdminLogin] = useState(false);
  const [adminPassword, setAdminPassword] = useState('');
  
  // --- ÉTATS CLIENT ---
  const [orderName, setOrderName] = useState('');
  const [discordName, setDiscordName] = useState('');
  const [quantity, setQuantity] = useState(1);
  const [format, setFormat] = useState('Barquette');
  const [sauceBlanche, setSauceBlanche] = useState('Non');
  const [sauceCurry, setSauceCurry] = useState('Non');
  const [sauceSupp, setSauceSupp] = useState('Rien');
  const [suppPoulet, setSuppPoulet] = useState('Non');
  const [soft, setSoft] = useState('Non');
  const [mode, setMode] = useState('Sur place');
  const [address, setAddress] = useState('');
  
  const [orderSuccess, setOrderSuccess] = useState(false);
  const [currentOrderCount, setCurrentOrderCount] = useState(0);

  // --- ÉTATS EMPLOYÉS ---
  const [orders, setOrders] = useState([]);
  const [adminTab, setAdminTab] = useState('NOUVELLES');
  const [searchQuery, setSearchQuery] = useState('');
  
  // Fausse base de données de fidélité (Pseudonyme -> Nombre de commandes)
  const [loyaltyDB, setLoyaltyDB] = useState({});

  // PRIX (Modifiables via panel si on voulait, ici en dur pour la démo)
  const prices = {
    barquette: 9.00,
    bol: 5.50,
    sauceSupp: 0.50,
    suppPoulet: 0.80,
    soft: 0.50
  };

  // --- CALCUL DU PRIX ---
  const calculateTotal = () => {
    let basePrice = format === 'Barquette' ? prices.barquette : prices.bol;
    if (sauceSupp !== 'Rien') basePrice += prices.sauceSupp;
    if (suppPoulet === 'Oui') basePrice += prices.suppPoulet;
    if (soft !== 'Non') basePrice += prices.soft;
    
    // Logique de gratuité (10ème gratuit)
    let userPastOrders = loyaltyDB[discordName.toLowerCase()] || 0;
    let itemsToPay = 0;
    
    for (let i = 0; i < quantity; i++) {
      if ((userPastOrders + i + 1) % 10 !== 0) {
        itemsToPay++;
      }
    }
    
    return basePrice * itemsToPay;
  };

  // --- SOUMISSION DE COMMANDE ---
  const handleSubmitOrder = (e) => {
    e.preventDefault();
    if (!orderName) return alert('Veuillez indiquer un nom de commande.');

    const total = calculateTotal();
    const newOrder = {
      id: Math.floor(Math.random() * 10000).toString().padStart(4, '0'),
      name: orderName,
      discord: discordName,
      quantity,
      format,
      sauceBlanche,
      sauceCurry,
      sauceSupp,
      suppPoulet,
      soft,
      mode,
      address,
      total,
      status: 'NOUVELLES',
      date: new Date().toLocaleDateString('fr-FR'),
      time: new Date().toLocaleTimeString('fr-FR')
    };

    setOrders([newOrder, ...orders]);
    
    // Mise à jour de la fidélité
    const currentLoyalty = loyaltyDB[discordName.toLowerCase()] || 0;
    const newLoyaltyCount = currentLoyalty + quantity;
    setLoyaltyDB({ ...loyaltyDB, [discordName.toLowerCase()]: newLoyaltyCount });
    
    setCurrentOrderCount(newLoyaltyCount % 10);
    setOrderSuccess(true);
    
    setTimeout(() => {
      setOrderSuccess(false);
      setOrderName('');
      setQuantity(1);
    }, 5000);
  };

  // --- LOGIQUE EMPLOYÉ ---
  const handleAdminLogin = (e) => {
    e.preventDefault();
    if (adminPassword === '18092026') {
      setIsAdmin(true);
      setShowAdminLogin(false);
      setAdminPassword('');
    } else {
      alert('Mot de passe incorrect');
    }
  };

  const advanceOrderStatus = (orderId, currentStatus, orderMode) => {
    const statusFlow = ['NOUVELLES', 'EN PRÉPARATION', 'PRÊTES'];
    if (orderMode === 'Livraison') {
      statusFlow.push('EN LIVRAISON');
    }
    statusFlow.push('TERMINÉES');

    const currentIndex = statusFlow.indexOf(currentStatus);
    if (currentIndex < statusFlow.length - 1) {
      const nextStatus = statusFlow[currentIndex + 1];
      setOrders(orders.map(o => o.id === orderId ? { ...o, status: nextStatus } : o));
    }
  };

  const generateDiscordTicket = (order) => {
    const ticket = `\`\`\`TASTY CROUSTY Avenue de la Résistance, 59000 Lille

Commande N° CB-${order.id}

NOM : ${order.name}
LIEU DE COMMANDE : ${order.mode === 'Livraison' ? order.address : 'SUR PLACE'}

TASTY CROUSTY ${order.format.toUpperCase()} x${order.quantity}       ${(order.format === 'Barquette' ? prices.barquette : prices.bol) * order.quantity}€
${order.sauceSupp !== 'Rien' ? `${order.sauceSupp.toUpperCase()}                       0,50€` : ''}
${order.soft !== 'Non' ? `${order.soft.toUpperCase()}                           0,50€` : ''}

- - - - - - - - - - - - - - - - -

TOTAL EUR TTC                    ${order.total.toFixed(2)}€

[PAYÉ PAR INTERNET]

CARTE BANCAIRE
VISA BANCAIRE

LE ${order.date} à ${order.time}

TASTY CROUSTY
59000
LILLE

COMMANDE CLIENT

À CONSERVER

- - - - - - - - - - - - - - - - -

TASTY CROUSTY LILLE\`\`\``;
    
    navigator.clipboard.writeText(ticket);
    alert('Ticket copié pour Discord !');
  };

  const filteredOrders = orders.filter(o => {
    const matchesTab = adminTab === 'TOUTES' || o.status === adminTab;
    const matchesSearch = o.name.toLowerCase().includes(searchQuery.toLowerCase()) || 
                          o.id.includes(searchQuery) ||
                          (o.discord && o.discord.toLowerCase().includes(searchQuery.toLowerCase()));
    return matchesTab && matchesSearch;
  });

  // --- RENDU ADMIN ---
  if (isAdmin) {
    return (
      <div className="min-h-screen bg-black text-white font-sans">
        <header className="bg-[#111] p-4 flex justify-between items-center border-b border-[#333]">
          <h1 className="text-xl font-bold text-[#FF0055]">PANEL EMPLOYÉ</h1>
          <button onClick={() => setIsAdmin(false)} className="bg-white text-black px-4 py-2 rounded-full text-sm font-bold">
            Retour au site
          </button>
        </header>

        <div className="p-4 overflow-x-auto flex space-x-2 bg-[#111]">
          {['TOUTES', 'NOUVELLES', 'EN PRÉPARATION', 'PRÊTES', 'EN LIVRAISON', 'TERMINÉES', 'STATISTIQUES'].map(tab => (
            <button 
              key={tab}
              onClick={() => setAdminTab(tab)}
              className={`px-4 py-2 rounded-full whitespace-nowrap font-bold text-sm transition-colors ${adminTab === tab ? 'bg-[#FF0055] text-white' : 'bg-[#222] text-gray-400'}`}
            >
              {tab}
            </button>
          ))}
        </div>

        <div className="p-4 max-w-6xl mx-auto">
          {adminTab === 'STATISTIQUES' ? (
            <div className="grid grid-cols-1 md:grid-cols-3 gap-4">
              <div className="bg-[#111] p-6 rounded-2xl border border-[#333]">
                <h3 className="text-gray-400 text-sm font-bold mb-2">COMMANDES TOTALES</h3>
                <p className="text-4xl font-bold text-white mb-4">{orders.length}</p>
                <div className="text-sm text-gray-500">
                  <p>Sur place : {orders.filter(o => o.mode === 'Sur place').length}</p>
                  <p>Livraison : {orders.filter(o => o.mode === 'Livraison').length}</p>
                </div>
              </div>
              <div className="bg-[#111] p-6 rounded-2xl border border-[#333]">
                <h3 className="text-gray-400 text-sm font-bold mb-2">TASTY COMMANDÉS</h3>
                <p className="text-4xl font-bold text-white mb-4">
                  {orders.reduce((acc, o) => acc + o.quantity, 0)}
                </p>
                <div className="text-sm text-gray-500">
                  <p>Barquettes : {orders.filter(o => o.format === 'Barquette').reduce((acc, o) => acc + o.quantity, 0)}</p>
                  <p>Bols : {orders.filter(o => o.format === 'Bol').reduce((acc, o) => acc + o.quantity, 0)}</p>
                </div>
              </div>
              <div className="bg-[#111] p-6 rounded-2xl border border-[#333]">
                <h3 className="text-gray-400 text-sm font-bold mb-2">CHIFFRE D'AFFAIRES</h3>
                <p className="text-4xl font-bold text-[#FF0055]">
                  {orders.reduce((acc, o) => acc + o.total, 0).toFixed(2)}€
                </p>
              </div>
            </div>
          ) : (
            <>
              <div className="mb-6 relative">
                <Search className="absolute left-3 top-3 text-gray-400" size="{20}"/>
                <input 
                  type="text" 
                  placeholder="Rechercher un nom, nº, etc..." 
                  className="w-full bg-[#111] border border-[#333] text-white p-3 pl-10 rounded-xl focus:border-[#FF0055] outline-none"
                  value={searchQuery}
                  onChange={(e) => setSearchQuery(e.target.value)}
                />
              </div>

              <div className="space-y-4">
                {filteredOrders.length === 0 ? (
                  <p className="text-center text-gray-500 py-10">Aucune commande trouvée.</p>
                ) : (
                  filteredOrders.map(order => (
                    <div key={order.id} className="bg-[#111] border border-[#333] rounded-2xl p-4 flex flex-col md:flex-row justify-between gap-4">
                      <div>
                        <div className="flex items-center gap-3 mb-2">
                          <span className="bg-[#FF0055] text-white px-2 py-1 rounded text-xs font-bold">#{order.id}</span>
                          <span className="font-bold text-lg">{order.name}</span>
                          <span className="text-sm text-gray-400">({order.mode})</span>
                        </div>
                        <p className="text-sm text-gray-400 mb-2">
                          {order.quantity}x {order.format} | Suppléments: {order.sauceSupp !== 'Rien' ? order.sauceSupp : 'Aucun'}, {order.suppPoulet === 'Oui' ? 'Poulet' : 'Sans poulet'} | Soft: {order.soft}
                        </p>
                        {order.mode === 'Livraison' && <p className="text-sm text-cyan-400">Adresse: {order.address}</p>}
                        {order.discord && <p className="text-sm text-[#5865F2]">Discord: {order.discord}</p>}
                      </div>
                      
                      <div className="flex flex-col gap-2 min-w-[200px]">
                        <div className="text-right mb-2">
                          <span className="text-xl font-bold">{order.total.toFixed(2)}€</span>
                        </div>
                        
                        {order.status !== 'TERMINÉES' && (
                          <button 
                            onClick={() => advanceOrderStatus(order.id, order.status, order.mode)}
                            className="bg-white text-black font-bold py-2 px-4 rounded-xl w-full flex justify-center items-center gap-2 hover:bg-gray-200"
                          >
                            <CheckCircle size="{18}"/>
                            Valider l'étape
                          </button>
                        )}
                        
                        <button 
                          onClick={() => generateDiscordTicket(order)}
                          className="bg-[#222] text-white border border-[#444] font-bold py-2 px-4 rounded-xl w-full flex justify-center items-center gap-2 hover:bg-[#333]"
                        >
                          Copier Ticket Discord
                        </button>
                      </div>
                    </div>
                  ))
                )}
              </div>
            </>
          )}
        </div>
      </div>
    );
  }

  // --- RENDU CLIENT ---
  return (
    <div className="bg-black text-white font-sans overflow-x-hidden">
      
      {/* HEADER FIXE */}
      <nav className="fixed top-0 w-full bg-black/90 backdrop-blur-md z-50 border-b border-[#333] p-4 flex justify-between items-center">
        <img src="image_10.png" alt="Tasty Crousty Logo" className="h-8 object-contain" />
        <a href="#commande" className="bg-[#FF0055] text-white px-5 py-2 rounded-full font-bold text-sm tracking-wide">
          COMMANDE TON TASTY
        </a>
      </nav>

      {/* HERO SECTION */}
      <section className="pt-32 pb-16 px-6 max-w-4xl mx-auto text-center">
        <h1 className="text-5xl md:text-7xl font-black tracking-tighter mb-6 uppercase leading-tight">
          L'ORIGINAL.<br/>LE SEUL.<br/><span className="text-[#FF0055]">LE N°1.</span>
        </h1>
        <p className="text-lg md:text-xl text-gray-300 mb-10 max-w-2xl mx-auto font-medium">
          Le bonheur est dans les choses simples — maintenant disponible dans GALAX RP, Lille virtuelle.
        </p>
        <div className="grid grid-cols-2 md:grid-cols-4 gap-4">
          <img src="image_2.png" alt="Ambiance 1" className="rounded-2xl object-cover h-40 w-full" />
          <img src="image_3.png" alt="Ambiance 2" className="rounded-2xl object-cover h-40 w-full" />
          <img src="image_4.png" alt="Ambiance 3" className="rounded-2xl object-cover h-40 w-full" />
          <img src="image.png" alt="Ambiance 4" className="rounded-2xl object-cover h-40 w-full" />
        </div>
      </section>

      {/* CONCEPT SECTION */}
      <section className="bg-white text-black py-20 px-6">
        <div className="max-w-4xl mx-auto">
          <span className="bg-[#FF0055] text-white px-4 py-1 rounded-full text-xs font-bold uppercase tracking-wider mb-6 inline-block">
            Chez Tasty Crousty
          </span>
          <h2 className="text-4xl md:text-5xl font-black mb-8 leading-tight">
            On vient se faire <span className="text-[#FF0055]">plaisir.</span><br/>C'est généreux.
          </h2>
          <p className="text-xl md:text-2xl font-medium mb-10 leading-relaxed text-gray-800">
            Une barquette <span className="text-cyan-500 font-bold">chaude</span>. Du riz <span className="text-cyan-500 font-bold">fondant</span>. Du poulet frit <span className="text-cyan-500 font-bold">ultra croustillant</span>. Une sauce maison <span className="text-cyan-500 font-bold">devenue culte</span>.
          </p>
          <div className="flex flex-col md:flex-row gap-8 items-center mt-16">
            <div className="flex-1">
              <h3 className="text-3xl font-black mb-4">Ingrédients XXL<br/>Générosité max<br/>Prix imbattable</h3>
              <p className="text-gray-600 font-medium">
                Zéro compromis sur ce qu'on sert. Zéro compromis sur l'expérience. Et pourtant, un prix volontairement imbattable.
              </p>
            </div>
            <div className="flex-1">
              <img src="image_5.png" alt="Ingrédients" className="rounded-3xl shadow-2xl w-full" />
            </div>
          </div>
        </div>
      </section>

      {/* STATS VIRALES */}
      <section className="bg-[#FF0055] py-20 px-6 text-white text-center">
        <div className="max-w-4xl mx-auto">
          <h2 className="text-4xl md:text-5xl font-black uppercase mb-12">Un phénomène<br/>viral international</h2>
          <div className="grid grid-cols-1 md:grid-cols-2 gap-4">
            {['+400 millions de vues', 'Des files d\'attente qui explosent', 'Les réseaux s\'enflamment', 'Les villes attendent leur ouverture'].map((text, i) => (
              <div key={i} className="bg-white text-black p-6 rounded-2xl flex items-center gap-4 font-bold text-lg">
                <CheckCircle className="text-[#FF0055]" size="{28}"/>
                <span>{text}</span>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* MAP SECTION */}
      <section className="bg-cyan-400 text-black py-20 px-6 text-center">
        <div className="max-w-4xl mx-auto">
          <h2 className="text-4xl md:text-6xl font-black uppercase mb-12">La Crousty Map</h2>
          <div className="bg-black p-2 rounded-3xl mb-6 shadow-2xl">
            <img src="image_9.png" alt="Map GALAX RP" className="rounded-2xl w-full h-auto object-cover" />
          </div>
          <div className="inline-flex items-center gap-2 bg-black text-white px-6 py-3 rounded-full font-bold">
            <MapPin className="text-[#FF0055]" size="{20}"/>
            <span>TASTY CROUSTY Lille - Avenue de la Resistance</span>
          </div>
        </div>
      </section>

      {/* COMMENT GOUTER */}
      <section className="py-20 px-6 max-w-4xl mx-auto">
        <div className="text-center mb-16">
          <span className="bg-[#FF0055] text-white px-4 py-1 rounded-full text-xs font-bold uppercase tracking-wider mb-6 inline-block">
            Comment goûter
          </span>
          <h2 className="text-4xl md:text-5xl font-black">Prêt à tester ?</h2>
          <p className="text-gray-400 mt-4 text-lg">Trois étapes. Quelques minutes. Et une barquette qui t'attend.</p>
        </div>
        
        <div className="space-y-6">
          {[
            { num: "1", title: "Trouve ton Tasty", desc: "Le Tasty Crousty de GALAX RP t'attend. Rends-toi sur place ou fais-toi livrer." },
            { num: "2", title: "Commande ta barquette", desc: "Passe ta commande directement ci-dessous. Quelques minutes pour préparer ta barquette." },
            { num: "3", title: "Maintenant savoure", desc: "Une barquette chaude, généreuse et croustillante. Prépare-toi à comprendre pourquoi." }
          ].map((step, i) => (
            <div key={i} className="bg-[#111] border border-[#333] p-8 rounded-3xl flex gap-6 items-start">
              <span className="text-6xl font-black text-[#FF0055] leading-none">{step.num}</span>
              <div>
                <h3 className="text-2xl font-bold mb-2">{step.title}</h3>
                <p className="text-gray-400 font-medium">{step.desc}</p>
              </div>
            </div>
          ))}
        </div>
      </section>

      {/* FORMULAIRE DE COMMANDE */}
      <section id="commande" className="py-20 px-6 bg-[#0a0a0a]">
        <div className="max-w-2xl mx-auto">
          <h2 className="text-4xl font-black mb-2 uppercase">Compose ton Tasty.</h2>
          <p className="text-gray-400 mb-10">Choisis tes options ci-dessous — le prix se calcule automatiquement.</p>
          
          {orderSuccess && (
            <div className="bg-[#FF0055] text-white p-6 rounded-3xl mb-8 text-center border-4 border-white shadow-[0_0_30px_rgba(255,0,85,0.5)]">
              <h3 className="text-2xl font-black uppercase mb-2">COMMANDE ENVOYÉE !</h3>
              <p className="font-bold text-lg mb-4">BONNE DÉGUSTATION !</p>
              <div className="bg-white text-black p-4 rounded-xl font-bold">
                VOUS ÊTES À {currentOrderCount}/9 D'OBTENIR UN 10ÈME TASTY CROUSTY GRATUIT !
              </div>
            </div>
          )}

          <form onSubmit={handleSubmitOrder} className="space-y-8 bg-black border border-[#333] p-6 md:p-10 rounded-3xl">
            
            {/* Nom & Discord */}
            <div className="space-y-4">
              <div>
                <label className="block text-sm font-bold text-gray-400 mb-2">TON NOM DE COMMANDE *</label>
                <input 
                  type="text" 
                  required
                  value={orderName}
                  onChange={(e) => setOrderName(e.target.value)}
                  className="w-full bg-[#111] border border-[#333] p-4 rounded-xl text-white font-bold focus:border-[#FF0055] outline-none transition-colors" 
                  placeholder="Ex: John Doe"
                />
              </div>
              <div>
                <label className="block text-sm font-bold text-gray-400 mb-2">TON PSEUDONYME DISCORD</label>
                <input 
                  type="text" 
                  value={discordName}
                  onChange={(e) => setDiscordName(e.target.value)}
                  className="w-full bg-[#111] border border-[#333] p-4 rounded-xl text-white font-bold focus:border-[#FF0055] outline-none transition-colors" 
                  placeholder="Ex: pseudo#1234"
                />
              </div>
            </div>

            {/* Quantité & Format */}
            <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
              <div>
                <label className="block text-sm font-bold text-gray-400 mb-2">QUANTITÉ</label>
                <div className="flex items-center gap-4 bg-[#111] border border-[#333] p-2 rounded-xl">
                  <button type="button" onClick={() => setQuantity(Math.max(1, quantity - 1))} className="p-2 bg-[#222] rounded-lg text-white hover:bg-[#333]">
                    <Minus size="{20}"/>
                  </button>
                  <input 
                    type="number" 
                    min="1" 
                    value={quantity}
                    onChange={(e) => setQuantity(Math.max(1, parseInt(e.target.value) || 1))}
                    className="w-full bg-transparent text-center font-black text-xl outline-none"
                  />
                  <button type="button" onClick={() => setQuantity(quantity + 1)} className="p-2 bg-[#222] rounded-lg text-white hover:bg-[#333]">
                    <Plus size="{20}"/>
                  </button>
                </div>
              </div>
              <div>
                <label className="block text-sm font-bold text-gray-400 mb-2">FORMAT *</label>
                <div className="flex gap-2">
                  <button type="button" onClick={() => setFormat('Barquette')} className={`flex-1 py-3 px-2 rounded-xl font-bold text-sm border ${format === 'Barquette' ? 'bg-[#FF0055] border-[#FF0055] text-white' : 'bg-[#111] border-[#333] text-gray-400 hover:border-gray-500'}`}>
                    Barquette (9,00€)
                  </button>
                  <button type="button" onClick={() => setFormat('Bol')} className={`flex-1 py-3 px-2 rounded-xl font-bold text-sm border ${format === 'Bol' ? 'bg-[#FF0055] border-[#FF0055] text-white' : 'bg-[#111] border-[#333] text-gray-400 hover:border-gray-500'}`}>
                    Bol (5,50€)
                  </button>
                </div>
              </div>
            </div>

            {/* Options */}
            <div className="space-y-6 pt-6 border-t border-[#222]">
              <div>
                <label className="block text-sm font-bold text-gray-400 mb-2">SAUCE SUPPLÉMENTAIRE (+0,50€)</label>
                <div className="flex flex-wrap gap-2">
                  {['Rien', 'Sauce sucrée', 'Sauce piquante', 'Sucrée & Piquante'].map(opt => (
                    <button key={opt} type="button" onClick={() => setSauceSupp(opt)} className={`py-2 px-4 rounded-xl font-bold text-sm border ${sauceSupp === opt ? 'bg-white text-black border-white' : 'bg-[#111] border-[#333] text-gray-400 hover:border-gray-500'}`}>
                      {opt}
                    </button>
                  ))}
                </div>
              </div>
              
              <div className="grid grid-cols-2 gap-6">
                <div>
                  <label className="block text-sm font-bold text-gray-400 mb-2">SUPPLÉMENT POULET (+0,80€)</label>
                  <div className="flex gap-2">
                    {['Non', 'Oui'].map(opt => (
                      <button key={opt} type="button" onClick={() => setSuppPoulet(opt)} className={`flex-1 py-2 rounded-xl font-bold text-sm border ${suppPoulet === opt ? 'bg-white text-black border-white' : 'bg-[#111] border-[#333] text-gray-400 hover:border-gray-500'}`}>
                        {opt}
                      </button>
                    ))}
                  </div>
                </div>
                <div>
                  <label className="block text-sm font-bold text-gray-400 mb-2">BOISSON SOFT (+0,50€)</label>
                  <div className="flex gap-2">
                    {['Non', 'Oui'].map(opt => (
                      <button key={opt} type="button" onClick={() => setSoft(opt)} className={`flex-1 py-2 rounded-xl font-bold text-sm border ${soft === opt ? 'bg-white text-black border-white' : 'bg-[#111] border-[#333] text-gray-400 hover:border-gray-500'}`}>
                        {opt}
                      </button>
                    ))}
                  </div>
                </div>
              </div>
            </div>

            {/* Mode de récupération */}
            <div className="pt-6 border-t border-[#222]">
              <label className="block text-sm font-bold text-gray-400 mb-2">MODE DE RÉCUPÉRATION *</label>
              <div className="flex gap-2 mb-4">
                <button type="button" onClick={() => setMode('Sur place')} className={`flex-1 py-4 rounded-xl font-bold border ${mode === 'Sur place' ? 'bg-cyan-500 text-black border-cyan-500' : 'bg-[#111] border-[#333] text-gray-400 hover:border-gray-500'}`}>
                  Sur place
                </button>
                <button type="button" onClick={() => setMode('Livraison')} className={`flex-1 py-4 rounded-xl font-bold border ${mode === 'Livraison' ? 'bg-cyan-500 text-black border-cyan-500' : 'bg-[#111] border-[#333] text-gray-400 hover:border-gray-500'}`}>
                  Livraison
                </button>
              </div>
              
              {mode === 'Livraison' && (
                <input 
                  type="text" 
                  required
                  value={address}
                  onChange={(e) => setAddress(e.target.value)}
                  className="w-full bg-[#111] border border-[#333] p-4 rounded-xl text-white font-bold focus:border-cyan-500 outline-none" 
                  placeholder="Adresse exacte dans GALAX RP"
                />
              )}
            </div>

            {/* Total et Validation */}
            <div className="bg-[#111] border border-[#333] p-6 rounded-2xl flex flex-col items-center mt-8">
              <span className="text-gray-400 font-bold mb-1">TOTAL À RÉGLER</span>
              <span className="text-5xl font-black text-[#FF0055] mb-6">{calculateTotal().toFixed(2)}€</span>
              <button type="submit" className="w-full bg-[#FF0055] text-white font-black py-4 rounded-xl text-lg uppercase tracking-wide hover:bg-pink-600 transition-colors">
                Envoyer ma commande
              </button>
            </div>
          </form>
        </div>
      </section>

      {/* FOOTER */}
      <footer className="bg-black py-12 px-6 border-t border-[#222] text-center relative">
        <img src="image_10.png" alt="Tasty Crousty" className="h-16 mx-auto mb-6 opacity-50 grayscale" />
        <p className="text-gray-500 text-sm font-bold tracking-widest uppercase">
          © 2026 TASTY CROUSTY - GALAX RP. MADE WITH LOVE BY @ourzon_ (DASSAULT Hugo)
        </p>

        {/* Cadenas caché pour admin */}
        <div className="mt-12 flex justify-center">
          <button onClick={() => setShowAdminLogin(!showAdminLogin)} className="text-[#222] hover:text-[#FF0055] transition-colors">
            <Lock size="{16}"/>
          </button>
        </div>
        
        {showAdminLogin && (
          <form onSubmit={handleAdminLogin} className="mt-4 flex justify-center gap-2">
            <input 
              type="password" 
              placeholder="Code accès" 
              value={adminPassword}
              onChange={(e) => setAdminPassword(e.target.value)}
              className="bg-[#111] border border-[#333] text-white px-4 py-2 rounded-lg text-sm outline-none"
            />
            <button type="submit" className="bg-[#FF0055] text-white px-4 py-2 rounded-lg text-sm font-bold">OK</button>
          </form>
        )}
      </footer>

    </div>
  );
};

export default App;
