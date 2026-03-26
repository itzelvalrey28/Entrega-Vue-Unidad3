<script>
export default {
  data() {
    return {
      // 1. Requisito Rúbrica: Vincular inputs a un objeto 'auto' en data()
      auto: {
        marca: '',
        modelo: '',
        año: '',
        color: '',
        precio: ''
      },
      // Estados para la interfaz
      mostrarGuardados: false,
      listaAutos: []
    }
  },
  methods: {
    // 2. Requisito Rúbrica: Prevenir recarga (@submit.prevent) y mostrar en consola
    registrarAuto() {
      // Verificación rápida para no guardar vacíos (aunque 'required' en HTML ayuda)
      if (!this.auto.marca || !this.auto.modelo) return;

      console.log("🚗 Objeto completo capturado:", this.auto);
      
      // Guardamos una copia independiente en la lista principal
      this.listaAutos.push({ ...this.auto });

      // Opcional: Limpiar formulario tras registrar (descomenta si quieres):
      // this.limpiarFormulario();
    },
    // 3. Requisito Rúbrica: Botón para limpiar (resetear objeto auto)
    limpiarFormulario() {
      this.auto = {
        marca: '',
        modelo: '',
        año: '',
        color: '',
        precio: ''
      };
      console.log("✨ Formulario reseteado.");
    },
    // Método para borrar un auto específico (Plus de funcionalidad)
    eliminarAuto(index) {
      this.listaAutos.splice(index, 1);
    }
  }
}
</script>

<template>
  <main class="container">
    
    <div v-if="!mostrarGuardados" class="layout">
      
      <section class="form-section">
        <h1 class="title">Registro de Vehículo</h1>
        
        <form @submit.prevent="registrarAuto">
          <input v-model="auto.marca" placeholder="Marca (ej. Ford)" type="text" required />
          <input v-model="auto.modelo" placeholder="Modelo (ej. Mustang)" type="text" required />
          
          <input v-model.number="auto.año" placeholder="Año (mínimo 1900)" type="number" min="1900" required />
          
          <input v-model="auto.color" placeholder="Color (ej. Rojo)" type="text" required />
          
          <input v-model.number="auto.precio" placeholder="Precio (ej. 55000.50)" type="number" step="0.01" required />
          
          <div class="button-group">
            <button type="submit" class="btn-main">Registrar Auto</button>
            <button type="button" @click="limpiarFormulario" class="btn-clean">Limpiar</button>
          </div>
          
          <button type="button" @click="mostrarGuardados = true" class="btn-secondary">
            Ver autos guardados ({{ listaAutos.length }})
          </button>
        </form>

        <div v-if="auto.marca || auto.modelo" class="preview-box">
          <h3>👀 Vista Previa (Reactividad):</h3>
          <p><strong>Marca:</strong> {{ auto.marca || '...' }}</p>
          <p><strong>Modelo:</strong> {{ auto.modelo || '...' }}</p>
          <p><strong>Año:</strong> {{ auto.año || '...' }}</p>
          <p><strong>Color:</strong> {{ auto.color || '...' }}</p>
          <p><strong>Precio:</strong> ${{ auto.precio || '0.00' }}</p>
        </div>
      </section>

      <section class="image-section">
        <img src="/corvette.jpg" alt="Corvette">
      </section>
    </div>

    <div v-else class="list-section">
      <h2 class="title">Autos en el Sistema ({{ listaAutos.length }})</h2>
      
      <div v-if="listaAutos.length > 0" class="grid">
        <div v-for="(item, index) in listaAutos" :key="index" class="card">
          <div class="card-header">
            <h3>{{ item.marca }} - {{ item.modelo }}</h3>
            <button @click="eliminarAuto(index)" class="btn-delete" title="Eliminar este auto">×</button>
          </div>
          <div class="card-body">
            <p><strong>Año:</strong> {{ item.año }}</p>
            <p><strong>Color:</strong> {{ item.color }}</p>
            <p><strong>Precio:</strong> ${{ item.precio }}</p>
          </div>
        </div>
      </div>
      
      <div v-else class="empty-state">
        <p>No hay autos registrados aún.</p>
        <p>Vuelve al formulario para agregar el primero.</p>
      </div>
      
      <button @click="mostrarGuardados = false" class="btn-main back-btn">Volver al Registro</button>
    </div>
  </main>
</template>

<style scoped>
/* ESTILOS GENERALES (Cumple con 'template limpio') */
.container { 
  background-color: #000; 
  color: white; 
  min-height: 100vh; 
  padding: 2rem; 
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; 
}

.title {
  color: #fff;
  font-weight: 300;
  margin-bottom: 2rem;
  border-left: 5px solid #e33422;
  padding-left: 15px;
}

/* LAYOUT DE REGISTRO */
.layout { 
  display: flex; 
  gap: 4rem; 
  justify-content: center; 
  align-items: flex-start; 
  max-width: 1200px;
  margin: 0 auto;
}

/* FORMULARIO */
form { 
  display: flex; 
  flex-direction: column; 
  gap: 15px; 
  width: 350px; 
}

input { 
  padding: 12px; 
  border-radius: 6px; 
  border: 1px solid #333; 
  background-color: #111;
  color: white;
  font-size: 1rem; 
  transition: border-color 0.2s;
}

input:focus {
  outline: none;
  border-color: #e33422;
}

/* BOTONES */
.button-group { 
  display: flex; 
  gap: 10px; 
}

.btn-main { 
  background-color: #e33422; 
  color: white; 
  padding: 12px; 
  border: none; 
  border-radius: 6px; 
  cursor: pointer; 
  flex: 2; 
  font-weight: bold; 
  font-size: 1rem;
  transition: background-color 0.2s;
}

.btn-main:hover {
  background-color: #c02a1b;
}

.btn-clean { 
  background-color: #333; 
  color: white; 
  border: none; 
  border-radius: 6px; 
  cursor: pointer; 
  flex: 1; 
}

.btn-clean:hover {
  background-color: #444;
}

.btn-secondary { 
  background-color: transparent; 
  border: 2px solid #e33422; 
  color: #e33422; 
  padding: 12px; 
  margin-top: 15px; 
  border-radius: 6px;
  cursor: pointer; 
  font-weight: bold;
}

.btn-secondary:hover {
  background-color: rgba(227, 52, 34, 0.1);
}

/* VISTA PREVIA (Reactividad Observable) */
.preview-box { 
  margin-top: 30px; 
  padding: 20px; 
  border: 2px dashed #444; 
  background: #0a0a0a; 
  border-radius: 10px; 
}

.preview-box h3 {
  color: #aaa;
  font-size: 1.1rem;
  margin-top: 0;
}

.preview-box p {
  margin: 10px 0;
  border-bottom: 1px solid #222;
  padding-bottom: 5px;
}

/* IMAGEN */
.image-section {
  display: flex;
  justify-content: center;
  align-items: center;
}

.image-section img { 
  max-width: 100%; 
  height: auto;
  border-radius: 15px; 
  box-shadow: 0 15px 40px rgba(0,0,0,0.7); 
}

/* LAYOUT DE LISTA GUARDADA (Responsivo y Detallado) */
.list-section {
  width: 100%;
  max-width: 1100px;
  margin: 0 auto;
  text-align: center;
}

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); 
  gap: 25px;
  margin: 40px 0;
}

.card {
  background: #111;
  border: 1px solid #333;
  border-radius: 12px;
  padding: 20px;
  text-align: left; 
  transition: transform 0.2s, border-color 0.2s;
}

.card:hover {
  transform: translateY(-8px);
  border-color: #e33422;
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 15px;
  border-bottom: 1px solid #222;
  padding-bottom: 10px;
}

.card-header h3 {
  color: #e33422;
  margin: 0;
  font-size: 1.3rem;
}

.btn-delete {
  background: none;
  border: none;
  color: #555;
  font-size: 1.5rem;
  cursor: pointer;
  line-height: 1;
}

.btn-delete:hover {
  color: #ff4444;
}

.card-body p {
  margin: 10px 0;
  font-size: 1rem;
  color: #bbb;
}

.card-body strong {
  color: white;
  margin-right: 5px;
}

.empty-state {
  margin: 60px 0;
  color: #666;
  font-size: 1.2rem;
}

.back-btn {
  width: 250px;
}
</style>