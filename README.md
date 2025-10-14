// No envio do lead, após montar o payload e enviar para o endpoint
try{
  await fetch('/api/leads', {
    method: 'POST',
    headers: {'Content-Type':'application/json'},
    body: JSON.stringify(payload)
  });
}catch(err){
  console.warn('Envio falhou (placeholder):', err);
}

// Enviar mensagem para WhatsApp do atendente da empresa
const waNumberAtendente = '5598984533013'; // número fixo do Daniel na ROD LIDER
const msgAtendente = encodeURIComponent(
  `Novo diagnóstico recebido:\n` +
  `Nome: ${state.nome}\n` +
  `WhatsApp: ${state.whatsapp}\n` +
  `Objetivo: ${state.objetivo} - ${state.sub}\n` +
  `Valor estimado: ${formatBR(state.valor)}\n` +
  `Parcela confortável: ${formatBR(state.parcela)}`
);
const waUrlAtendente = `https://wa.me/${waNumberAtendente}?text=${msgAtendente}`;

// Avança para obrigado e abre WhatsApp do atendente em nova aba
goStep(6);
setTimeout(() => window.open(waUrlAtendente, '_blank'), 1000);
