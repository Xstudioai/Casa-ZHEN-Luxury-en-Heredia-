import React, { useState, useEffect } from 'react';
import { Leaf, Wind, Maximize2, MapPin, Car, Waves, ChevronDown, Phone, Mail, Instagram, Menu, X } from 'lucide-react';

// --- CONFIGURACIÓN DE ESTILO ---
// Fondo: bg-[#FAFAF8] (Blanco Hueso / Papel Arroz)
// Texto Principal: text-[#2C2C2C] (Carbón Suave)
// Acentos: text-[#8C7B6C] (Bronce/Tierra)

const UnfriedLuxuryEstate = () => {
  const [scrolled, setScrolled] = useState(false);
  const [mobileMenuOpen, setMobileMenuOpen] = useState(false);
  const [activeImage, setActiveImage] = useState(null);

  // Mapeo exacto de las imágenes subidas
  const images = {
    hero: "1000453972.jpg",     // Fachada principal / Entrada
    facade: "1000453971.jpg",   // Fachada
    living: "1000453970.jpg",   // Sala
    kitchen: "1000453967.jpg",  // Cocina
    terrace: "1000453968.jpg",  // Terraza
    bathroom: "1000453969.jpg", // Baño
    bedroom: "1000453966.jpg",  // Cuarto
    rooftop: "1000453963.jpg",  // Azotea
    garden: "1000453975.jpg",   // Jardín
    detail: "1000453964.jpg",   // Detalle
  };

  useEffect(() => {
    const handleScroll = () => {
      setScrolled(window.scrollY > 20);
    };
    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, []);

  const features = [
    { icon: <Maximize2 size={18} />, label: "Terreno", value: "512 m²" },
    { icon: <Wind size={18} />, label: "Construcción", value: "350 m²" },
    { icon: <Car size={18} />, label: "Cochera", value: "4 Autos" },
    { icon: <Waves size={18} />, label: "Relax", value: "Jacuzzi" },
  ];

  const handleWhatsapp = () => {
    window.open(`https://wa.me/50686455050?text=Hola, estoy interesado en la casa de lujo en San Pedro de Barva.`, '_blank');
  };

  return (
    <div className="min-h-screen bg-[#FAFAF8] text-[#2C2C2C] font-sans selection:bg-[#DBCFB0] selection:text-white pb-20 md:pb-0">
      
      {/* --- NAVEGACIÓN (Responsive) --- */}
      <nav className={`fixed top-0 w-full z-50 transition-all duration-500 border-b ${scrolled ? 'bg-[#FAFAF8]/95 backdrop-blur-md border-[#E5E5E5] py-3' : 'bg-transparent border-transparent py-4 md:py-6'}`}>
        <div className="container mx-auto px-4 md:px-8 flex justify-between items-center">
          {/* Logo / Marca */}
          <div className={`flex flex-col z-50 ${scrolled ? 'text-[#2C2C2C]' : 'text-white mix-blend-difference'}`}>
            <span className="text-lg md:text-xl font-serif tracking-widest font-bold uppercase">Unfried</span>
            <span className="text-[0.6rem] md:text-xs tracking-[0.3em] uppercase opacity-80">Bienes Raíces</span>
          </div>

          {/* Menú Desktop */}
          <div className="hidden md:flex items-center gap-6">
            <button onClick={handleWhatsapp} className={`px-6 py-2 border text-xs tracking-widest uppercase transition-all hover:bg-white hover:text-black ${scrolled ? 'border-[#2C2C2C] text-[#2C2C2C]' : 'border-white text-white'}`}>
              Agendar Cita
            </button>
          </div>

          {/* Botón Móvil */}
          <button className="md:hidden z-50 text-[#2C2C2C] p-2 bg-white/80 rounded-full backdrop-blur-sm" onClick={handleWhatsapp}>
            <Phone size={20} />
          </button>
        </div>
      </nav>

      {/* --- HERO SECTION --- */}
      <header className="relative h-[85vh] md:h-screen w-full overflow-hidden">
        {/* Imagen de fondo con overlay para legibilidad */}
        <div className="absolute inset-0">
          <img 
            src={images.hero} 
            alt="Fachada Principal" 
            className="w-full h-full object-cover object-center animate-[pulse_30s_ease-in-out_infinite_alternate]" 
          />
          <div className="absolute inset-0 bg-gradient-to-t from-[#FAFAF8] via-black/20 to-black/40"></div>
        </div>

        {/* Contenido Hero */}
        <div className="relative z-10 h-full flex flex-col justify-center items-center text-center px-4 pt-20">
          <p className="text-white/90 text-xs md:text-sm tracking-[0.3em] uppercase mb-4 animate-fade-in-up">
            San Pedro de Barva, Heredia
          </p>
          <h1 className="text-4xl md:text-6xl lg:text-8xl font-serif text-white mb-6 leading-tight shadow-sm">
            Equilibrio <br/> <span className="italic font-light opacity-90">& Permanencia</span>
          </h1>
          <div className="h-12 w-px bg-white/60 mx-auto mb-6"></div>
          <p className="text-white font-light text-xl md:text-2xl tracking-wide">
            $360,000 USD
          </p>
          
          <div className="absolute bottom-8 left-1/2 -translate-x-1/2 text-white/60 animate-bounce">
            <ChevronDown size={28} />
          </div>
        </div>
      </header>

      {/* --- CONCEPTO ZEN --- */}
      <section className="py-16 md:py-24 px-4 md:px-8 bg-[#FAFAF8]">
        <div className="max-w-4xl mx-auto text-center">
          <Leaf className="mx-auto mb-6 text-[#8C7B6C]" size={24} strokeWidth={1} />
          <h2 className="text-2xl md:text-4xl font-serif text-[#2C2C2C] mb-6 leading-relaxed">
            Un santuario privado entre la naturaleza y el lujo moderno.
          </h2>
          <p className="text-[#666] text-base md:text-lg leading-loose font-light mb-12 text-justify md:text-center px-2">
            Esta residencia de 350 m² redefine la vida en Barva. Diseñada para invocar la calma, 
            cuenta con terrazas que respiran, una azotea mirador sobre la sala de doble altura 
            y acabados que susurran elegancia en cada rincón.
          </p>

          {/* Grid de Características (Responsive: 2x2 en móvil, 4x1 en desktop) */}
          <div className="grid grid-cols-2 md:grid-cols-4 gap-6 md:gap-12 border-t border-b border-[#E5E5E5] py-8 md:py-12">
            {features.map((feature, idx) => (
              <div key={idx} className="flex flex-col items-center justify-center p-2">
                <div className="text-[#8C7B6C] mb-2">{feature.icon}</div>
                <span className="text-[10px] md:text-xs uppercase tracking-widest text-[#999] mb-1">{feature.label}</span>
                <span className="font-serif text-lg md:text-xl text-[#2C2C2C]">{feature.value}</span>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* --- GALERÍA MOSAICO RESPONSIVE --- */}
      <section className="py-8 md:py-12 px-4 max-w-[1600px] mx-auto">
        {/* Mobile: Columna simple (Stack) | Desktop: Grid Mosaico */}
        <div className="grid grid-cols-1 md:grid-cols-12 gap-4 auto-rows-[300px] md:auto-rows-[400px]">
          
          {/* Sala Principal - Destacada */}
          <div className="md:col-span-8 md:row-span-2 relative group overflow-hidden rounded-sm cursor-pointer" onClick={() => setActiveImage(images.living)}>
            <img src={images.living} alt="Sala" className="w-full h-full object-cover transition-transform duration-700 group-hover:scale-105" />
            <div className="absolute bottom-0 left-0 right-0 p-6 bg-gradient-to-t from-black/60 to-transparent">
              <p className="text-white text-xs uppercase tracking-widest mb-1">Espacios Comunes</p>
              <h3 className="text-white font-serif text-2xl">Luz & Doble Altura</h3>
            </div>
          </div>

          {/* Cocina */}
          <div className="md:col-span-4 relative group overflow-hidden rounded-sm cursor-pointer" onClick={() => setActiveImage(images.kitchen)}>
             <img src={images.kitchen} alt="Cocina" className="w-full h-full object-cover transition-transform duration-700 group-hover:scale-105" />
             <div className="absolute inset-0 flex items-center justify-center bg-black/20 opacity-0 group-hover:opacity-100 transition-opacity">
                <span className="text-white font-serif">Cocina Gourmet</span>
             </div>
          </div>

          {/* Terraza */}
          <div className="md:col-span-4 relative group overflow-hidden rounded-sm cursor-pointer" onClick={() => setActiveImage(images.terrace)}>
            <img src={images.terrace} alt="Terraza" className="w-full h-full object-cover transition-transform duration-700 group-hover:scale-105" />
          </div>

          {/* Habitación */}
           <div className="md:col-span-5 md:row-span-2 relative group overflow-hidden rounded-sm cursor-pointer" onClick={() => setActiveImage(images.bedroom)}>
            <img src={images.bedroom} alt="Habitación" className="w-full h-full object-cover transition-transform duration-700 group-hover:scale-105" />
             <div className="absolute bottom-0 left-0 right-0 p-6 bg-gradient-to-t from-black/60 to-transparent">
              <h3 className="text-white font-serif text-xl">Descanso Profundo</h3>
            </div>
          </div>

          {/* Azotea / Texto Promocional */}
          <div className="md:col-span-7 bg-[#E8E6E1] flex flex-col items-center justify-center p-8 text-center rounded-sm">
             <Wind className="text-[#8C7B6C] mb-4" size={32} />
             <h3 className="font-serif text-2xl md:text-3xl text-[#2C2C2C] mb-2">El Mirador Privado</h3>
             <p className="text-[#666] font-light text-sm md:text-base max-w-md">
               Una azotea exclusiva con jacuzzi y vistas panorámicas. El lugar perfecto para desconectar del mundo exterior.
             </p>
          </div>
          
           {/* Baño */}
           <div className="md:col-span-4 relative group overflow-hidden rounded-sm cursor-pointer" onClick={() => setActiveImage(images.bathroom)}>
            <img src={images.bathroom} alt="Baño" className="w-full h-full object-cover transition-transform duration-700 group-hover:scale-105" />
          </div>

           {/* Fachada 2 */}
           <div className="md:col-span-8 relative group overflow-hidden rounded-sm cursor-pointer" onClick={() => setActiveImage(images.facade)}>
            <img src={images.facade} alt="Exterior" className="w-full h-full object-cover transition-transform duration-700 group-hover:scale-105" />
          </div>

        </div>
      </section>

      {/* --- LISTA DE AMENIDADES (Diseño limpio) --- */}
      <section className="py-16 md:py-24 bg-white px-4 md:px-8">
        <div className="max-w-6xl mx-auto flex flex-col md:flex-row gap-12">
          
          <div className="md:w-1/3">
            <span className="text-xs font-bold tracking-[0.2em] text-[#8C7B6C] uppercase block mb-4">La Propiedad</span>
            <h2 className="text-3xl md:text-4xl font-serif text-[#2C2C2C] mb-6">Detalles de Lujo</h2>
            <div className="w-16 h-1 bg-[#2C2C2C] mb-6"></div>
          </div>
          
          <div className="md:w-2/3 grid grid-cols-1 gap-8">
            {/* Item 1 */}
            <div className="flex gap-4 group">
              <div className="mt-1 min-w-[20px] text-[#8C7B6C]">•</div>
              <div>
                <h4 className="font-serif text-xl text-[#2C2C2C] mb-2 group-hover:text-[#8C7B6C] transition-colors">Interiores</h4>
                <p className="text-[#666] font-light leading-relaxed text-sm">
                  Sala y comedor integrados con doble altura, cocina moderna, cuarto principal con walking closet, 2 cuartos secundarios, 2.5 baños de lujo.
                </p>
              </div>
            </div>

            {/* Item 2 */}
            <div className="flex gap-4 group">
              <div className="mt-1 min-w-[20px] text-[#8C7B6C]">•</div>
              <div>
                <h4 className="font-serif text-xl text-[#2C2C2C] mb-2 group-hover:text-[#8C7B6C] transition-colors">Exteriores & Ocio</h4>
                <p className="text-[#666] font-light leading-relaxed text-sm">
                  Cochera techada para 2 vehículos (+2 en pista), 2 terrazas, 3 balcones, amplia bodega y hermosas zonas verdes.
                </p>
              </div>
            </div>

            {/* Item 3 */}
            <div className="flex gap-4 group">
              <div className="mt-1 min-w-[20px] text-[#8C7B6C]">•</div>
              <div>
                <h4 className="font-serif text-xl text-[#2C2C2C] mb-2 group-hover:text-[#8C7B6C] transition-colors">Ubicación</h4>
                <p className="text-[#666] font-light leading-relaxed text-sm">
                  Barrio tranquilo y seguro en San Pedro de Barva, calle pública asfaltada con todos los servicios.
                </p>
              </div>
            </div>
          </div>

        </div>
      </section>

      {/* --- CONTACTO / FOOTER --- */}
      <footer className="bg-[#1C1C1C] text-white py-16 px-6">
        <div className="container mx-auto flex flex-col md:flex-row justify-between items-center md:items-start text-center md:text-left gap-10">
          
          {/* Brand Footer */}
          <div>
            <h2 className="text-2xl md:text-3xl font-serif tracking-wide mb-2">Unfried</h2>
            <p className="text-xs uppercase tracking-[0.3em] text-[#8C7B6C] mb-6">Bienes Raíces</p>
            <p className="text-white/40 font-light text-sm max-w-xs mx-auto md:mx-0">
              Expertos en propiedades exclusivas en la zona de Heredia y alrededores.
            </p>
          </div>

          {/* Botones de Acción */}
          <div className="flex flex-col gap-4 w-full md:w-auto">
             <div className="text-center md:text-right mb-2">
                <span className="block text-xs uppercase tracking-widest text-[#8C7B6C]">Precio de Venta</span>
                <span className="font-serif text-2xl">$360,000 USD</span>
             </div>
             
             <button onClick={handleWhatsapp} className="flex items-center justify-center gap-3 bg-[#DBCFB0] text-[#1C1C1C] px-8 py-4 w-full md:w-auto hover:bg-white transition-colors">
               <Phone size={18} /> 
               <span className="text-xs font-bold tracking-widest uppercase">Llamar: 8645-5050</span>
             </button>
             
             <button onClick={handleWhatsapp} className="flex items-center justify-center gap-3 border border-white/20 px-8 py-4 w-full md:w-auto hover:bg-white/10 transition-colors">
               <Mail size={18} />
               <span className="text-xs font-bold tracking-widest uppercase">WhatsApp Directo</span>
             </button>
          </div>
        </div>
        
        <div className="mt-12 pt-8 border-t border-white/10 text-center text-[10px] text-white/30 uppercase tracking-widest">
          © 2024 Unfried Bienes Raíces. Todos los derechos reservados.
        </div>
      </footer>

      {/* --- BARRA INFERIOR FIJA (Solo Móvil) --- */}
      <div className="md:hidden fixed bottom-0 left-0 w-full bg-white border-t border-gray-200 z-50 flex">
        <button onClick={handleWhatsapp} className="flex-1 py-4 flex flex-col items-center justify-center text-[#2C2C2C] active:bg-gray-50">
           <Phone size={20} className="mb-1"/>
           <span className="text-[10px] uppercase tracking-widest font-bold">Llamar</span>
        </button>
        <button onClick={handleWhatsapp} className="flex-1 py-4 flex flex-col items-center justify-center bg-[#2C2C2C] text-white active:bg-black">
           <span className="text-[10px] uppercase tracking-widest font-bold">WhatsApp</span>
        </button>
      </div>

      {/* --- LIGHTBOX (Visor de Imágenes) --- */}
      {activeImage && (
        <div className="fixed inset-0 z-[100] bg-black/95 flex items-center justify-center p-4 backdrop-blur-sm" onClick={() => setActiveImage(null)}>
          <button className="absolute top-4 right-4 text-white/70 hover:text-white p-2">
            <X size={32} />
          </button>
          <img src={activeImage} alt="Detalle" className="max-w-full max-h-[80vh] shadow-2xl object-contain" />
        </div>
      )}

    </div>
  );
};

export default UnfriedLuxuryEstate;

