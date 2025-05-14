import React, { useState } from 'react';
import { Card, CardContent } from '@/components/ui/card';
import { Button } from '@/components/ui/button';
import { Calendar } from 'lucide-react';

export default function App() {
  const [events, setEvents] = useState([
    { id: 1, title: 'Culto de Maturidade', date: 'Quinta-feira 10:30', confirmed: false },
    
    { id: 2, title: 'Culto da Família', date: 'Domingo 19:00', confirmed: false },
    
    { id: 3, title: 'Mulheres em Plenitude', date: 'Última Sexta-feira do Mês 10:30', confirmed: false },
    
    { id: 4, title: 'Homens em Plenitude', date: 'Última Sexta-feira do Mês 10:30', confirmed: false },
    
    { id: 5, title: 'Culto de Santa Ceia', date: 'Segundo Domingo 10:00', confirmed: false },
    
    { id: 6, title: 'Jovens em Plenitude', date: 'Sábado 15:00', confirmed: false },
    
    { id: 7, title: 'Café da Comunhão', date: 'Terceiro Domingo do Mês 09:00', confirmed: false },
    
    { id: 8, title: 'Peace at Home', date: 'Quarta-feira 19:00', confirmed: false },
    
    { id: 9, title: 'Reunião Ministerial', date: 'Primeiro Sábado do Mês 19:00', confirmed: false }
  ]);

  const [prayerRequests, setPrayerRequests] = useState([
  
    { id: 1, content: 'Oração pela saúde de Maria', urgent: false },
    
    { id: 2, content: 'Oração por um novo emprego', urgent: true }
  ]);

  const [devotionals, setDevotionals] = useState([
    { id: 1, title: 'Confiança em Deus', content: 'Salmo 37:5 - Entrega o teu caminho ao Senhor...', favorite: false },
    
    { id: 2, title: 'Perdão e Graça', content: 'Mateus 6:14 - Porque se perdoardes...', favorite: false },
    
    { id: 3, title: 'Devocional Jovens em Plenitude', content: '1 Timóteo 4:12 - Ninguém despreze a tua mocidade...', favorite: false },
    
    { id: 4, title: 'Devocional Casais em Plenitude', content: 'Efésios 5:33 - Cada um de vocês ame a sua esposa como a si mesmo...', favorite: false },
    
    { id: 5, title: 'Devocional Homens em Plenitude', content: '1 Coríntios 16:13 - Vigiai, estai firmes na fé, portai-vos varonilmente...', favorite: false },
    
    { id: 6, title: 'Devocional Mulheres em Plenitude', content: 'Provérbios 31:25 - Força e dignidade são os seus vestidos...', favorite: false },
    
    { id: 7, title: 'Devocional Plenitude Kids', content: 'Salmo 127:3 - Os filhos são herança do Senhor...', favorite: false }
  ]);

  const confirmAttendance = (id) => {
    setEvents(events.map(event => event.id === id ? { ...event, confirmed: !event.confirmed } : event));
  };

  return (
    <div className="p-4 bg-gray-100 min-h-screen">
      <h1 className="text-2xl font-bold mb-4">Engajamento da Comunidade</h1>

      <section className="mb-6">
        <h2 className="text-xl font-semibold mb-2">Eventos</h2>
        {events.map(event => (
          <Card key={event.id} className="mb-2">
            <CardContent className="flex justify-between">
              <div>
                <p className="font-semibold">{event.title}</p>
                <p className="text-gray-500">{event.date}</p>
              </div>
              <Button onClick={() => confirmAttendance(event.id)}>
                {event.confirmed ? 'Presença Confirmada' : 'Confirmar Presença'}
              </Button>
            </CardContent>
          </Card>
        ))}
      </section>

      <section className="mb-6">
        <h2 className="text-xl font-semibold mb-2">Pedidos de Oração</h2>
        {prayerRequests.map(request => (
          <Card key={request.id} className="mb-2">
            <CardContent>
              <p className={request.urgent ? 'text-red-500' : ''}>{request.content}</p>
            </CardContent>
          </Card>
        ))}
      </section>

      <section>
        <h2 className="text-xl font-semibold mb-2">Devocionais Diários</h2>
        {devotionals.map(devotional => (
          <Card key={devotional.id} className="mb-2">
            <CardContent>
              <h3 className="font-semibold mb-1">{devotional.title}</h3>
              <p>{devotional.content}</p>
            </CardContent>
          </Card>
        ))}
      </section>
    </div>
  );
}

// Ajuste para GitHub Pages
// Adicione no package.json: "homepage": "https://seuusuario.github.io/nome-do-repositorio"
// Para build e deploy:
// npm run build
// npm install -g gh-pages
// npm run deploy
