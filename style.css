const tabButtons = document.querySelectorAll(".tab-button");
const tabContents = document.querySelectorAll(".tab-content");

tabButtons.forEach(btn => {
    btn.addEventListener("click", () => {
        const target = btn.getAttribute("data-tab");

        tabButtons.forEach(b => b.classList.remove("active"));
        btn.classList.add("active");

        tabContents.forEach(content => {
            content.classList.remove("active");
            if (content.id === target) {
                content.classList.add("active");
            }
        });
    });
});

/*Dunas Dunas*/
// --- Verificar selección múltiple ---
function verificarMultiples(btn, correctas) {
    const checkboxes = btn.parentElement.querySelectorAll('input[type="checkbox"]');
    let seleccionadas = [];
    checkboxes.forEach(ch => {
        if (ch.checked) seleccionadas.push(ch.value);
    });

    const correctasStr = correctas.sort().join(',');
    const seleccionadasStr = seleccionadas.sort().join(',');

    if (correctasStr === seleccionadasStr) {
        btn.insertAdjacentHTML('afterend', '<p class="correcto">✅ ¡Excelente!</p>');
    } else {
        btn.insertAdjacentHTML('afterend', '<p class="incorrecto">❌ Revisa tus respuestas.</p>');
    }

    btn.disabled = true;
}

// --- Emparejar (drag & drop) ---
const draggables = document.querySelectorAll('.draggable');
const drops = document.querySelectorAll('.drop');

draggables.forEach(el => {
    el.addEventListener('dragstart', e => {
        e.dataTransfer.setData('text/plain', el.dataset.value);
    });
});

drops.forEach(el => {
    el.addEventListener('dragover', e => e.preventDefault());
    el.addEventListener('drop', e => {
        const valor = e.dataTransfer.getData('text/plain');
        if (valor === el.dataset.correct) {
            el.classList.add('correcto');
            el.innerHTML += ` ✅ (${valor})`;
        } else {
            el.classList.add('incorrecto');
            el.innerHTML += ` ❌ (${valor})`;
        }
    });
});


/*Dunas Dunas*/


/*minerologia*/
// --- Ordenar lista ---
function verificarOrden(id, ordenCorrecto) {
  const lista = document.querySelector(`#${id}`);
  const items = Array.from(lista.children).map(li => li.textContent.trim());
  if (JSON.stringify(items) === JSON.stringify(ordenCorrecto)) {
    lista.insertAdjacentHTML('afterend', '<p class="correcto">✅ ¡Orden perfecto!</p>');
  } else {
    lista.insertAdjacentHTML('afterend', '<p class="incorrecto">❌ Revisa el orden.</p>');
  }
}

// Permitir drag en lista ordenable
document.querySelectorAll('.ordenar').forEach(lista => {
  let dragItem = null;
  lista.addEventListener('dragstart', e => dragItem = e.target);
  lista.addEventListener('dragover', e => e.preventDefault());
  lista.addEventListener('drop', e => {
    if (e.target.tagName === 'LI' && e.target !== dragItem) {
      lista.insertBefore(dragItem, e.target.nextSibling);
    }
  });
});

/*minerologia*/

/*Montaña*/// ===== Drag & Drop reutilizable (ya usado en Dunas/Rocas) =====
// (si ya existe, no hace falta repetir; este fragmento asegura listeners para nuevos draggables/drops)
function initDragDropEnSection(sectionId) {
  const section = document.querySelector(sectionId);
  if (!section) return;

  const draggables = section.querySelectorAll('.draggable');
  const drops = section.querySelectorAll('.drop');

  draggables.forEach(el => {
    el.addEventListener('dragstart', e => {
      e.dataTransfer.setData('text/plain', el.dataset.value);
    });
  });

  drops.forEach(el => {
    el.addEventListener('dragover', e => e.preventDefault());
    el.addEventListener('drop', e => {
      const valor = e.dataTransfer.getData('text/plain');
      if (valor === el.dataset.correct) {
        el.classList.add('correcto');
        el.innerHTML += ` ✅ (${valor})`;
      } else {
        el.classList.add('incorrecto');
        el.innerHTML += ` ❌ (${valor})`;
      }
    });
  });
}

// Inicializa al cargar
window.addEventListener('load', () => {
  initDragDropEnSection('#montanas');
});

// ===== Actividad de campo: marcar completado =====
function marcarActividadesCampo(btn) {
  const container = btn.parentElement;
  const checks = container.querySelectorAll('.campo-check');
  const realizadas = [];
  checks.forEach(c => { if (c.checked) realizadas.push(c.value); });
  const result = document.getElementById('campo-result');
  if (realizadas.length === 0) {
    result.innerHTML = '<p class="incorrecto">Marca al menos una actividad.</p>';
  } else {
    result.innerHTML = `<p class="correcto">✅ Actividad(s) completada(s): ${realizadas.join(', ')}</p>`;
  }
  btn.disabled = true;
}

// ===== Generador de idea de juego =====
function generarIdeaJuego() {
  const ideas = [
    'Race to the Summit: equipo compite por responder 10 preguntas sobre formación de montañas y gana quien llegue a la cima.',
    'Mapa interactivo: colocar pines en un mapa (local) para ubicar montañas estudiadas y explicar su historia.',
    'Puzzle de elevaciones: ordenar montañas por altura y ganar estrellas por velocidad y exactitud.'
  ];
  const idea = ideas[Math.floor(Math.random() * ideas.length)];
  document.getElementById('idea-juego').textContent = idea;
}


/*Montaña*/

/*Ecologia*/
// Inicializa drag/drop para ecologia (si ya existe initDragDropEnSection, se reutiliza)
window.addEventListener('load', () => { initDragDropEnSection('#ecologia'); });

// Toggle para informe
function toggleText(id) {
  const el = document.getElementById(id);
  if (!el) return;
  el.style.display = (el.style.display === 'none') ? 'block' : 'none';
}

// Generar recomendación sobre basura
function generarInformeBasura() {
  const kg = parseFloat(document.getElementById('kgFamilia').value) || 0;
  const reco = document.getElementById('recoleccion').value || 'No ingresado';
  const out = document.getElementById('basura-result');
  let texto = `Estimación: ${kg.toFixed(2)} kg/familia/día. Recolección: ${reco}. `;
  if (kg > 2) texto += 'Volumen alto: proponer programas de compostaje y reciclaje. ';
  else texto += 'Volumen razonable: mantener separación y educación. ';
  if (reco === 'Malo') texto += 'Sugerencia inmediata: puntos de acopio y campañas de denuncia.';
  out.innerHTML = `<p class="nota">${texto}</p>`;
}

// Graficar calidad del aire en canvas (simple)
function dibujarGraficaAire() {
  const vals = [];
  for (let i=1;i<=7;i++) vals.push(parseFloat(document.getElementById('d'+i).value) || 0);
  const canvas = document.getElementById('graf-air');
  const ctx = canvas.getContext('2d');
  ctx.clearRect(0,0,canvas.width,canvas.height);
  // Ejes
  ctx.beginPath(); ctx.moveTo(30,10); ctx.lineTo(30,130); ctx.lineTo(310,130); ctx.strokeStyle = '#ccc'; ctx.stroke();
  // Max
  const max = Math.max(...vals,10);
  // Line
  ctx.beginPath();
  vals.forEach((v,i)=>{
    const x = 40 + i*36;
    const y = 130 - (v / max) * 100;
    if (i===0) ctx.moveTo(x,y); else ctx.lineTo(x,y);
    // puntos
    ctx.fillStyle='#2e7d32'; ctx.beginPath(); ctx.arc(x,y,3,0,2*Math.PI); ctx.fill();
    ctx.fillText(v.toString(), x-8, y-8);
  });
  ctx.strokeStyle='#388e3c'; ctx.stroke();
  ctx.fillStyle='#000'; ctx.fillText('PM2.5 (µg/m³) 7 días', 100, 12);
}

/*Ecologia*/


/*Energía renovable*/
 // Verdadero / Falso
document.querySelectorAll('.vf').forEach(el => {
    el.addEventListener('click', () => {
        const correcto = el.dataset.correcta === 'verdadero';
        const eleccion = confirm("¿Verdadero o Falso?");
        const acierto = (eleccion && correcto) || (!eleccion && !correcto);
        el.classList.remove('correcto', 'incorrecto');
        el.classList.add(acierto ? 'correcto' : 'incorrecto');
    });
});

// Selección múltiple
document.querySelectorAll('.pregunta').forEach(p => {
    const correcta = p.dataset.correcta;
    p.querySelectorAll('button').forEach(btn => {
        btn.addEventListener('click', () => {
            p.querySelectorAll('button').forEach(b => b.disabled = true);
            btn.classList.add(btn.textContent === correcta ? 'correcto' : 'incorrecto');
        });
    });
});

// Arrastrar y soltar
document.querySelectorAll('.drag').forEach(drag => {
    drag.addEventListener('dragstart', e => {
        e.dataTransfer.setData('text/plain', drag.dataset.target);
        drag.classList.add('dragging');
    });
    drag.addEventListener('dragend', () => drag.classList.remove('dragging'));
});

document.querySelectorAll('.drop').forEach(drop => {
    drop.addEventListener('dragover', e => e.preventDefault());
    drop.addEventListener('drop', e => {
        const data = e.dataTransfer.getData('text/plain');
        if (data === drop.dataset.accept) {
            drop.classList.add('ok');
            drop.textContent += " ✅";
            const dragging = document.querySelector('.drag.dragging');
            if (dragging) dragging.style.visibility = 'hidden';
        } else {
            drop.classList.add('fail');
            setTimeout(() => drop.classList.remove('fail'), 1000);
        }
    });
});

/*Energía renovable*/


/*pantanos*/
// ✅ Verdadero/Falso
document.querySelectorAll('.vf-question').forEach(q => {
  q.addEventListener('click', () => {
    const answer = q.dataset.answer === "true";
    const choice = confirm(`¿Crees que esto es Verdadero?`);
    q.classList.remove('correct', 'incorrect');
    if (choice === answer) {
      q.classList.add('correct');
    } else {
      q.classList.add('incorrect');
    }
  });
});

// ✅ Selección múltiple
document.querySelectorAll('.quiz .option').forEach(btn => {
  btn.addEventListener('click', () => {
    const correct = btn.dataset.correct === "true";
    btn.parentNode.querySelectorAll('.option').forEach(b => b.disabled = true);
    btn.classList.add(correct ? 'correct' : 'incorrect');
  });
});

// ✅ Arrastrar y Soltar
const drags = document.querySelectorAll('.drag');
const drops = document.querySelectorAll('.drop');

drags.forEach(drag => {
  drag.addEventListener('dragstart', e => {
    e.dataTransfer.setData('text', drag.dataset.match);
  });
});

drops.forEach(drop => {
  drop.addEventListener('dragover', e => e.preventDefault());
  drop.addEventListener('drop', e => {
    e.preventDefault();
    const dragged = e.dataTransfer.getData('text');
    if (dragged === drop.dataset.accept) {
      drop.classList.add('correct');
      drop.textContent += " ✅";
    } else {
      drop.classList.add('wrong');
      drop.textContent += " ❌";
    }
  });
});

/*pantanos*/
