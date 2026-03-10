  import React, { useState, useEffect } from 'react';
import { Truck, Package, ShieldCheck, Clock, Phone, Mail, MapPin, Menu, X, Wrench, CheckCircle } from 'lucide-react';
import { Button } from '../components/ui/button';
import { Card, CardContent } from '../components/ui/card';
import { Input } from '../components/ui/input';
import { Textarea } from '../components/ui/textarea';
import { useToast } from '../hooks/use-toast';
import { mockData } from '../mock';

const Home = () => {
  const [isMenuOpen, setIsMenuOpen] = useState(false);
  const [formData, setFormData] = useState({ name: '', email: '', phone: '', message: '' });
  const { toast } = useToast();

  const handleSubmit = (e) => {
    e.preventDefault();
    toast({
      title: "Mensagem enviada com sucesso!",
      description: "Entraremos em contato em breve.",
    });
    setFormData({ name: '', email: '', phone: '', message: '' });
  };

  const scrollToSection = (id) => {
    const element = document.getElementById(id);
    if (element) {
      element.scrollIntoView({ behavior: 'smooth' });
      setIsMenuOpen(false);
    }
  };

  return (
    <div className="min-h-screen bg-white">
      {/* Header */}
      <header className="fixed top-0 left-0 right-0 z-50 bg-white/95 backdrop-blur-md shadow-md">
        <div className="container mx-auto px-4">
          <div className="flex items-center justify-between h-20">
            <div className="flex items-center space-x-3">
              <div className="w-12 h-12 bg-gradient-to-br from-red-600 to-red-700 rounded-lg flex items-center justify-center">
                <Truck className="w-7 h-7 text-white" />
              </div>
              <div>
                <h1 className="text-xl font-bold text-gray-900 leading-tight">Casa das Molas</h1>
                <p className="text-xs text-gray-600">O Dedé</p>
              </div>
            </div>

            {/* Desktop Menu */}
            <nav className="hidden md:flex items-center space-x-8">
              <button onClick={() => scrollToSection('inicio')} className="text-gray-700 hover:text-red-600 transition-colors font-medium">Início</button>
              <button onClick={() => scrollToSection('sobre')} className="text-gray-700 hover:text-red-600 transition-colors font-medium">Sobre</button>
              <button onClick={() => scrollToSection('produtos')} className="text-gray-700 hover:text-red-600 transition-colors font-medium">Produtos</button>
              <button onClick={() => scrollToSection('contato')} className="text-gray-700 hover:text-red-600 transition-colors font-medium">Contato</button>
              <Button onClick={() => scrollToSection('contato')} className="bg-red-600 hover:bg-red-700 text-white">Solicitar Orçamento</Button>
            </nav>

            {/* Mobile Menu Button */}
            <button onClick={() => setIsMenuOpen(!isMenuOpen)} className="md:hidden p-2">
              {isMenuOpen ? <X className="w-6 h-6" /> : <Menu className="w-6 h-6" />}
            </button>
          </div>

          {/* Mobile Menu */}
          {isMenuOpen && (
            <div className="md:hidden py-4 border-t animate-in slide-in-from-top">
              <nav className="flex flex-col space-y-3">
                <button onClick={() => scrollToSection('inicio')} className="text-left px-4 py-2 text-gray-700 hover:bg-red-50 hover:text-red-600 transition-colors rounded">Início</button>
                <button onClick={() => scrollToSection('sobre')} className="text-left px-4 py-2 text-gray-700 hover:bg-red-50 hover:text-red-600 transition-colors rounded">Sobre</button>
                <button onClick={() => scrollToSection('produtos')} className="text-left px-4 py-2 text-gray-700 hover:bg-red-50 hover:text-red-600 transition-colors rounded">Produtos</button>
                <button onClick={() => scrollToSection('contato')} className="text-left px-4 py-2 text-gray-700 hover:bg-red-50 hover:text-red-600 transition-colors rounded">Contato</button>
              </nav>
            </div>
          )}
        </div>
      </header>

      {/* Hero Section */}
      <section id="inicio" className="relative pt-20 min-h-screen flex items-center overflow-hidden">
        <div 
          className="absolute inset-0 z-0"
          style={{
            backgroundImage: `url('${mockData.images.hero}')`,
            backgroundSize: 'cover',
            backgroundPosition: 'center',
          }}
        >
          <div className="absolute inset-0 bg-gradient-to-r from-gray-900/95 via-gray-900/85 to-transparent"></div>
        </div>
        
        <div className="container mx-auto px-4 relative z-10">
          <div className="max-w-3xl">
            <div className="inline-block mb-6 px-4 py-2 bg-red-600/20 backdrop-blur-sm border border-red-500/30 rounded-full">
              <span className="text-red-400 font-semibold text-sm">✓ Mais de 15 anos de experiência</span>
            </div>
            <h1 className="text-5xl md:text-7xl font-bold text-white mb-6 leading-tight animate-in fade-in slide-in-from-bottom duration-700">
              Peças de Qualidade para seu Caminhão
            </h1>
            <p className="text-xl md:text-2xl text-gray-200 mb-8 leading-relaxed animate-in fade-in slide-in-from-bottom duration-700 delay-150">
              Molas, buchas, grampos e muito mais. Atendimento especializado e estoque completo.
            </p>
            <div className="flex flex-col sm:flex-row gap-4 animate-in fade-in slide-in-from-bottom duration-700 delay-300">
              <Button onClick={() => scrollToSection('contato')} size="lg" className="bg-red-600 hover:bg-red-700 text-white text-lg px-8 py-6 shadow-xl hover:shadow-2xl transition-all hover:scale-105">
                Solicitar Orçamento
              </Button>
              <Button onClick={() => scrollToSection('produtos')} size="lg" variant="outline" className="border-2 border-white text-white hover:bg-white hover:text-gray-900 text-lg px-8 py-6 transition-all">
                Ver Produtos
              </Button>
            </div>
            
            {/* Stats */}
            <div className="grid grid-cols-3 gap-6 mt-16 pt-8 border-t border-white/20">
              <div className="text-center">
                <div className="text-4xl font-bold text-yellow-400 mb-2">15+</div>
                <div className="text-gray-300 text-sm">Anos no Mercado</div>
              </div>
              <div className="text-center">
                <div className="text-4xl font-bold text-yellow-400 mb-2">500+</div>
                <div className="text-gray-300 text-sm">Produtos</div>
              </div>
              <div className="text-center">
                <div className="text-4xl font-bold text-yellow-400 mb-2">24h</div>
                <div className="text-gray-300 text-sm">Atendimento</div>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* About Section */}
      <section id="sobre" className="py-24 bg-gray-50">
        <div className="container mx-auto px-4">
          <div className="max-w-3xl mx-auto text-center mb-16">
            <h2 className="text-4xl md:text-5xl font-bold text-gray-900 mb-6">Sobre a Casa das Molas O Dedé</h2>
            <p className="text-xl text-gray-600 leading-relaxed">
              Somos uma distribuidora especializada em peças para caminhões, com foco em qualidade, variedade e atendimento excepcional.
            </p>
          </div>

          <div className="grid md:grid-cols-3 gap-8">
            <Card className="border-none shadow-lg hover:shadow-xl transition-all hover:-translate-y-1 duration-300">
              <CardContent className="p-8">
                <div className="w-16 h-16 bg-blue-100 rounded-2xl flex items-center justify-center mb-6">
                  <ShieldCheck className="w-8 h-8 text-blue-600" />
                </div>
                <h3 className="text-2xl font-bold text-gray-900 mb-4">Qualidade Garantida</h3>
                <p className="text-gray-600 leading-relaxed">
                  Trabalhamos apenas com fornecedores certificados e produtos de primeira linha.
                </p>
              </CardContent>
            </Card>

            <Card className="border-none shadow-lg hover:shadow-xl transition-all hover:-translate-y-1 duration-300">
              <CardContent className="p-8">
                <div className="w-16 h-16 bg-yellow-100 rounded-2xl flex items-center justify-center mb-6">
                  <Package className="w-8 h-8 text-yellow-600" />
                </div>
                <h3 className="text-2xl font-bold text-gray-900 mb-4">Estoque Completo</h3>
                <p className="text-gray-600 leading-relaxed">
                  Ampla variedade de peças para diversos modelos e marcas de caminhões.
                </p>
              </CardContent>
            </Card>

            <Card className="border-none shadow-lg hover:shadow-xl transition-all hover:-translate-y-1 duration-300">
              <CardContent className="p-8">
                <div className="w-16 h-16 bg-red-100 rounded-2xl flex items-center justify-center mb-6">
                  <Clock className="w-8 h-8 text-red-600" />
                </div>
                <h3 className="text-2xl font-bold text-gray-900 mb-4">Atendimento Rápido</h3>
                <p className="text-gray-600 leading-relaxed">
                  Agilidade no atendimento e entrega para manter seu caminhão sempre na estrada.
                </p>
              </CardContent>
            </Card>
          </div>
        </div>
      </section>

      {/* Products Section */}
      <section id="produtos" className="py-24 bg-white">
        <div className="container mx-auto px-4">
          <div className="max-w-3xl mx-auto text-center mb-16">
            <h2 className="text-4xl md:text-5xl font-bold text-gray-900 mb-6">Nossos Produtos</h2>
            <p className="text-xl text-gray-600 leading-relaxed">
              Peças de alta qualidade para manter seu caminhão em perfeito funcionamento.
            </p>
          </div>

          <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
            {mockData.products.map((product, index) => (
              <Card key={index} className="border-2 border-gray-100 hover:border-red-500 transition-all hover:shadow-xl group">
                <CardContent className="p-0">
                  <div className="aspect-video bg-gradient-to-br from-gray-100 to-gray-200 flex items-center justify-center overflow-hidden">
                    <Wrench className="w-20 h-20 text-gray-400 group-hover:text-red-600 transition-all group-hover:scale-110 duration-300" />
                  </div>
                  <div className="p-6">
                    <h3 className="text-2xl font-bold text-gray-900 mb-3">{product.name}</h3>
                    <p className="text-gray-600 mb-4 leading-relaxed">{product.description}</p>
                    <Button onClick={() => scrollToSection('contato')} variant="outline" className="w-full border-2 border-red-600 text-red-600 hover:bg-red-600 hover:text-white transition-all">
                      Solicitar Orçamento
                    </Button>
                  </div>
                </CardContent>
              </Card>
            ))}
          </div>
        </div>
      </section>

      {/* Why Choose Us */}
      <section className="py-24 bg-gradient-to-br from-blue-50 to-red-50">
        <div className="container mx-auto px-4">
          <div className="max-w-3xl mx-auto text-center mb-16">
            <h2 className="text-4xl md:text-5xl font-bold text-gray-900 mb-6">Por Que Escolher a Casa das Molas?</h2>
          </div>

          <div className="grid md:grid-cols-2 lg:grid-cols-4 gap-6 max-w-5xl mx-auto">
            {mockData.benefits.map((benefit, index) => (
              <div key={index} className="bg-white rounded-xl p-6 shadow-lg hover:shadow-xl transition-all hover:-translate-y-1">
                <CheckCircle className="w-12 h-12 text-green-500 mb-4" />
                <h4 className="text-lg font-bold text-gray-900 mb-2">{benefit.title}</h4>
                <p className="text-gray-600 text-sm">{benefit.description}</p>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Contact Section */}
      <section id="contato" className="py-24 bg-white">
        <div className="container mx-auto px-4">
          <div className="max-w-3xl mx-auto text-center mb-16">
            <h2 className="text-4xl md:text-5xl font-bold text-gray-900 mb-6">Entre em Contato</h2>
            <p className="text-xl text-gray-600 leading-relaxed">
              Estamos prontos para atendê-lo. Envie sua mensagem ou visite nossa loja.
            </p>
          </div>

          <div className="grid lg:grid-cols-2 gap-12 max-w-6xl mx-auto">
            {/* Contact Info */}
            <div className="space-y-8">
              <Card className="border-none shadow-lg">
                <CardContent className="p-8">
                  <div className="flex items-start space-x-4">
                    <div className="w-12 h-12 bg-red-100 rounded-lg flex items-center justify-center flex-shrink-0">
                      <Phone className="w-6 h-6 text-red-600" />
                    </div>
                    <div>
                      <h3 className="text-lg font-bold text-gray-900 mb-2">Telefone</h3>
                      <p className="text-gray-600">{mockData.contact.phone}</p>
                    </div>
                  </div>
                </CardContent>
              </Card>

              <Card className="border-none shadow-lg">
                <CardContent className="p-8">
                  <div className="flex items-start space-x-4">
                    <div className="w-12 h-12 bg-blue-100 rounded-lg flex items-center justify-center flex-shrink-0">
                      <Mail className="w-6 h-6 text-blue-600" />
                    </div>
                    <div>
                      <h3 className="text-lg font-bold text-gray-900 mb-2">Email</h3>
                      <p className="text-gray-600">{mockData.contact.email}</p>
                    </div>
                  </div>
                </CardContent>
              </Card>

              <Card className="border-none shadow-lg">
                <CardContent className="p-8">
                  <div className="flex items-start space-x-4">
                    <div className="w-12 h-12 bg-yellow-100 rounded-lg flex items-center justify-center flex-shrink-0">
                      <MapPin className="w-6 h-6 text-yellow-600" />
                    </div>
                    <div>
                      <h3 className="text-lg font-bold text-gray-900 mb-2">Endereço</h3>
                      <p className="text-gray-600">{mockData.contact.address}</p>
                    </div>
                  </div>
                </CardContent>
              </Card>

              <Card className="border-none shadow-lg">
                <CardContent className="p-8">
                  <div className="flex items-start space-x-4">
                    <div className="w-12 h-12 bg-green-100 rounded-lg flex items-center justify-center flex-shrink-0">
                      <Clock className="w-6 h-6 text-green-600" />
                    </div>
                    <div>
                      <h3 className="text-lg font-bold text-gray-900 mb-2">Horário de Funcionamento</h3>
                      <p className="text-gray-600">{mockData.contact.hours.weekday}</p>
                      <p className="text-gray-600">{mockData.contact.hours.saturday}</p>
                      <p className="text-gray-600">{mockData.contact.hours.sunday}</p>
                    </div>
                  </div>
                </CardContent>
              </Card>
            </div>

            {/* Contact Form */}
            <Card className="border-none shadow-xl">
              <CardContent className="p-8">
                <h3 className="text-2xl font-bold text-gray-900 mb-6">Envie sua Mensagem</h3>
                <form onSubmit={handleSubmit} className="space-y-6">
                  <div>
                    <label className="block text-sm font-semibold text-gray-700 mb-2">Nome</label>
                    <Input
                      type="text"
                      value={formData.name}
                      onChange={(e) => setFormData({ ...formData, name: e.target.value })}
                      placeholder="Seu nome"
                      required
                      className="h-12"
                    />
                  </div>
                  <div>
                    <label className="block text-sm font-semibold text-gray-700 mb-2">Email</label>
                    <Input
                      type="email"
                      value={formData.email}
                      onChange={(e) => setFormData({ ...formData, email: e.target.value })}
                      placeholder="seu@email.com"
                      required
                      className="h-12"
                    />
                  </div>
                  <div>
                    <label className="block text-sm font-semibold text-gray-700 mb-2">Telefone</label>
                    <Input
                      type="tel"
                      value={formData.phone}
                      onChange={(e) => setFormData({ ...formData, phone: e.target.value })}
                      placeholder="(86) 99999-9999"
                      required
                      className="h-12"
                    />
                  </div>
                  <div>
                    <label className="block text-sm font-semibold text-gray-700 mb-2">Mensagem</label>
                    <Textarea
                      value={formData.message}
                      onChange={(e) => setFormData({ ...formData, message: e.target.value })}
                      placeholder="Como podemos ajudá-lo?"
                      required
                      rows={5}
                    />
                  </div>
                  <Button type="submit" className="w-full bg-red-600 hover:bg-red-700 text-white h-12 text-lg font-semibold">
                    Enviar Mensagem
                  </Button>
                </form>
              </CardContent>
            </Card>
          </div>
        </div>
      </section>

      {/* Footer */}
      <footer className="bg-gray-900 text-white py-12">
        <div className="container mx-auto px-4">
          <div className="grid md:grid-cols-3 gap-8 mb-8">
            <div>
              <div className="flex items-center space-x-3 mb-4">
                <div className="w-12 h-12 bg-red-600 rounded-lg flex items-center justify-center">
                  <Truck className="w-7 h-7 text-white" />
                </div>
                <div>
                  <h3 className="text-xl font-bold">Casa das Molas</h3>
                  <p className="text-sm text-gray-400">O Dedé</p>
                </div>
              </div>
              <p className="text-gray-400 leading-relaxed">
                Distribuidora especializada em peças para caminhões com qualidade e confiança.
              </p>
            </div>

            <div>
              <h4 className="text-lg font-bold mb-4">Links Rápidos</h4>
              <ul className="space-y-2">
                <li><button onClick={() => scrollToSection('inicio')} className="text-gray-400 hover:text-white transition-colors">Início</button></li>
                <li><button onClick={() => scrollToSection('sobre')} className="text-gray-400 hover:text-white transition-colors">Sobre</button></li>
                <li><button onClick={() => scrollToSection('produtos')} className="text-gray-400 hover:text-white transition-colors">Produtos</button></li>
                <li><button onClick={() => scrollToSection('contato')} className="text-gray-400 hover:text-white transition-colors">Contato</button></li>
              </ul>
            </div>

            <div>
              <h4 className="text-lg font-bold mb-4">Contato</h4>
              <ul className="space-y-3 text-gray-400">
                <li className="flex items-center space-x-2">
                  <Phone className="w-4 h-4" />
                  <span>{mockData.contact.phone}</span>
                </li>
                <li className="flex items-center space-x-2">
                  <Mail className="w-4 h-4" />
                  <span>{mockData.contact.email}</span>
                </li>
                <li className="flex items-start space-x-2">
                  <MapPin className="w-4 h-4 mt-1" />
                  <span>{mockData.contact.address}</span>
                </li>
              </ul>
            </div>
          </div>

          <div className="border-t border-gray-800 pt-8 text-center">
            <p className="text-gray-400">
              © 2025 Distribuidora Casa das Molas O Dedé. Todos os direitos reservados.
            </p>
          </div>
        </div>
      </footer>

      {/* WhatsApp Float Button */}
      <a
        href={`https://wa.me/5586995627829`}
        target="_blank"
        rel="noopener noreferrer"
        className="fixed bottom-6 right-6 z-50 w-16 h-16 bg-green-500 hover:bg-green-600 rounded-full flex items-center justify-center shadow-2xl hover:scale-110 transition-all animate-bounce"
      >
        <Phone className="w-8 h-8 text-white" />
      </a>
    </div>
  );
};

export default Home;
