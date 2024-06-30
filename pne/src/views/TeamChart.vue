<template>
    <div class="team-chart-container">
      <h1 class="header-text">فريق إدارة البيتزا</h1>
      <div v-if="isLoading" class="loading-spinner">جار التحميل...</div>
      <div v-else class="team-chart">
        <!-- Lucas at the top -->
        <div class="section">
          <a v-for="member in lucas" :key="member.id" :href="'https://wa.me/' + member.phone.replace(/[\s()-]/g, '')" target="_blank" rel="noopener noreferrer" class="card manager-card">
            <img :src="getImagePath(member.first_name)" alt="member photo" class="member-image" />
            <h4>{{ member.first_name }} {{ member.last_name }}</h4>
            <p>{{ member.position_name }}</p>
          </a>
        </div>
  
        <!-- BigSam and Emma -->
        <div class="section row">
          <a v-for="member in pmMembers" :key="member.id" :href="'https://wa.me/' + member.phone.replace(/[\s()-]/g, '')" target="_blank" rel="noopener noreferrer" class="card manager-card">
            <img :src="getImagePath(member.first_name)" alt="member photo" class="member-image" />
            <h4>{{ member.first_name }} {{ member.last_name }}</h4>
            <p>{{ member.position_name }}</p>
          </a>
        </div>
        
        <!-- Divider after BigSam and Emma -->
        <hr class="divider" />
  
        <!-- Robert and Malcolm -->
        <div class="section row">
          <a v-for="member in maintenanceAndMarketingMembers" :key="member.id" :href="'https://wa.me/' + member.phone.replace(/[\s()-]/g, '')" target="_blank" rel="noopener noreferrer" class="card manager-card">
            <img :src="getImagePath(member.first_name)" alt="member photo" class="member-image" />
            <h4>{{ member.first_name }} {{ member.last_name }}</h4>
            <p>{{ member.position_name }}</p>
          </a>
        </div>
        
        <!-- Divider after Robert and Malcolm -->
        <hr class="divider" />
  
        <!-- Samantha and Sarah -->
        <div class="section row">
          <a v-for="member in adminAffairsMembers" :key="member.id" :href="'https://wa.me/' + member.phone.replace(/[\s()-]/g, '')" target="_blank" rel="noopener noreferrer" class="card manager-card">
            <img :src="getImagePath(member.first_name)" alt="member photo" class="member-image" />
            <h4>{{ member.first_name }} {{ member.last_name }}</h4>
            <p>{{ member.position_name }}</p>
          </a>
        </div>
        
        <!-- Divider after Samantha and Sarah -->
        <hr class="divider" />
  
        <!-- Rashill and Cyntia -->
        <div class="section row">
          <a v-for="member in legalMembers" :key="member.id" :href="'https://wa.me/' + member.phone.replace(/[\s()-]/g, '')" target="_blank" rel="noopener noreferrer" class="card manager-card">
            <img :src="getImagePath(member.first_name)" alt="member photo" class="member-image" />
            <h4>{{ member.first_name }} {{ member.last_name }}</h4>
            <p>{{ member.position_name }}</p>
          </a>
        </div>
        
        <!-- Divider after Rashill and Cyntia -->
        <hr class="divider" />
  
        <!-- Group Managers and their Stores -->
        <div v-for="group in groupManagers" :key="group.groupId" class="section">
          <h2 class="group-name">{{ group.groupName }}</h2>
          <div class="group-container">
            <div class="group-managers row">
              <a v-for="manager in group.managers" :key="manager.id" :href="'https://wa.me/' + manager.phone.replace(/[\s()-]/g, '')" target="_blank" rel="noopener noreferrer" class="group-manager-card card">
                <img :src="getImagePath(manager.first_name)" alt="group manager photo" class="member-image" />
                <h4>{{ manager.first_name }} {{ manager.last_name }}</h4>
                <p>{{ manager.position_name }}</p>
              </a>
            </div>
            <div class="stores">
              <a v-for="store in group.stores" :key="store.id" :href="'https://wa.me/' + store.phone.replace(/[\s()-]/g, '')" target="_blank" rel="noopener noreferrer" class="card store-card">
                <img src="../assets/mp/lc.jpg" alt="store photo" class="member-image" />
                <h4>{{ store.first_name }} {{ store.last_name }}</h4>
                <p>{{ store.position_name }}</p>
              </a>
            </div>
          </div>
          <!-- Divider after each group -->
          <hr class="divider" />
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import managers from '@/assets/managers-ar.json';
  
  // Import all images statically
  import مالكوم from '@/assets/mp/Malcolm.png';
  import روبيرت from '@/assets/mp/Robert.jpg';
  import الين from '@/assets/mp/Alan.png';
  import ليو from '@/assets/mp/Leo.png';
  import آنّا from '@/assets/mp/Anna.jpg';
  import بيغسام from '@/assets/mp/Bigsam.png';
  import براين from '@/assets/mp/Bryan.png';
  import سينتيا from '@/assets/mp/Cyntia.png';
  import إيما from '@/assets/mp/Emma.png';
  import إستفان from '@/assets/mp/Estefan.png';
  import جيمي from '@/assets/mp/Jimmy.png';
  import جو from '@/assets/mp/Joe.png';
  import جوزيف from '@/assets/mp/Joseph.png';
  import كييث from '@/assets/mp/Keith.png';
  import لوكاس from '@/assets/mp/Lucas.png';
  import سامانثا from '@/assets/mp/Samantha.png';
  import ساره from '@/assets/mp/Sarah.png';
  import ستيفاني from '@/assets/mp/Stephanie.png';
  import راشيل from '@/assets/mp/Rashill.png';
  
  export default {
    data() {
      return {
        team: managers.Data,
        isLoading: false,
        images: {
          الين,
          راشيل,
          آنّا,
          ليو,
          بيغسام,
          براين,
          سينتيا,
          إيما,
          إستفان,
          جيمي,
          جو,
          جوزيف,
          كييث,
          لوكاس,
          مالكوم,
          روبيرت,
          سامانثا,
          ساره,
          ستيفاني
        }
      };
    },
    computed: {
      lucas() {
        return this.team.filter(member => member.first_name === 'لوكاس');
      },
      pmMembers() {
        return this.team.filter(member => member.position_name === 'مدير البرنامج');
      },
      adminAffairsMembers() {
        return this.team.filter(member => member.position_name === 'الشؤون الإدارية');
      },
      legalMembers() {
        return this.team.filter(member => member.position_name === 'قانون');
      },
      maintenanceAndMarketingMembers() {
        return this.team.filter(
          member => ['الصيانة', 'التسويق'].includes(member.position_name)
        );
      },
      groupManagers() {
        return [
          {
            groupId: 1,
            groupName: 'مجموعة 1',
            managers: this.team.filter(m => m.group_id === 1 && m.position_name === 'مدير المجموعة' ),
            stores: this.team.filter(m => m.group_id === 1 && m.position_name === 'مدير المتجر')
          },
          {
            groupId: 2,
            groupName: 'مجموعة 2',
            managers: this.team.filter(m => m.group_id === 2 && m.position_name === 'مدير المجموعة'),
            stores: this.team.filter(m => m.group_id === 2 && m.position_name === 'مدير المتجر')
          },
          {
            groupId: 3,
            groupName: 'مجموعة 3',
            managers: this.team.filter(m => m.group_id === 3 && m.position_name === 'مدير المجموعة'),
            stores: this.team.filter(m => m.group_id === 3 && m.position_name === 'مدير المتجر')
          },
          {
            groupId: 4,
            groupName: 'مجموعة 4',
            managers: this.team.filter(m => m.group_id === 4 && m.position_name === 'مدير المجموعة'),
            stores: this.team.filter(m => m.group_id === 4 && m.position_name === 'مدير المتجر')
          },
          {
            groupId: 5,
            groupName: 'مجموعة 5',
            managers: this.team.filter(m => m.group_id === 5 && m.position_name === 'مدير المجموعة'),
            stores: this.team.filter(m => m.group_id === 5 && m.position_name === 'مدير المتجر')
          }
        ];
      }
    },
    methods: {
      showDetails(member) {
        alert(`Name: ${member.first_name} ${member.last_name}\nRole: ${member.position_name}\nPhone: ${member.phone}`);
      },
      getImagePath(firstName) {
        return this.images[firstName] || 'https://picsum.photos/80';
      }
    }
  };
  </script>
  
  <style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap');
  
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  
  body {
    font-family: 'Cairo', sans-serif;
    background-color: #121212;
    color: #e0e0e0;
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
  }
  
  .team-chart-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    max-width: 1200px;
    padding: 20px;
  }
  
  .header-text {
    margin-bottom: 20px;
    font-size: 2.5rem;
    color: #ffffff;
    text-align: center;
  }
  
  .team-chart {
    align-items: center;
    width: 100%;
  }
  
  .section {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-bottom: 20px;
  }
  
  .section.row {
    flex-direction: row;
    justify-content: center; /* Center content horizontally */
  }
  
  .group-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
  }
  
  .group-container.row {
    flex-direction: row;
    flex-wrap: wrap;
  }
  
  .group-manager {
    text-align: center;
    margin-bottom: 10px;
  }
  
  .stores {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
  
  .card {
    background: #1e1e1e;
    border: 1px solid #333;
    padding: 10px;
    margin: 10px;
    border-radius: 8px;
    width: 100%;
    max-width: 150px;
    text-align: center;
    transition: transform 0.2s, box-shadow 0.2s;
    text-decoration: none;
    color: #e0e0e0;
    font-size: 0.9rem; /* Smaller text size */
  }
  
  .card h4 {
    font-size: 1rem; /* Smaller text size for names */
  }
  
  .card p {
    font-size: 0.8rem; /* Smaller text size for positions */
  }
  
  .card:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 15px rgba(0, 0, 0, 0.2);
  }
  
  .group-managers {
    display: flex;
    flex-direction: row;
    justify-content: center; /* Center content horizontally */
  }
  
  .group-manager-card {
    background: #1e1e1e;
    border: 1px solid #333;
    padding: 10px;
    margin: 10px;
    border-radius: 8px;
    width: 100%;
    max-width: 150px;
    text-align: center;
    transition: transform 0.2s, box-shadow 0.2s;
    text-decoration: none;
    color: #e0e0e0;
    font-size: 0.9rem; /* Smaller text size */
  }
  
  .group-manager-card h4 {
    font-size: 1rem; /* Smaller text size for names */
  }
  
  .group-manager-card p {
    font-size: 0.8rem; /* Smaller text size for positions */
  }
  
  .group-manager-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 15px rgba(0, 0, 0, 0.2);
  }
  
  .member-image {
    border-radius: 50%;
    width: 60px;
    height: 60px;
    object-fit: cover;
    margin-bottom: 10px;
  }
  
  .loading-spinner {
    text-align: center;
    font-size: 1.8rem;
    padding: 20px;
  }
  
  .divider {
    width: 100%;
    border: 1px solid #444;
    margin: 20px 0;
  }
  
  .small-divider {
    width: 80%;
    border: 1px solid #333;
    margin: 10px 0;
  }
  
  .group-name {
    font-size: 1.3rem; /* Smaller text size */
    color: #ffffff;
    margin-bottom: 10px;
    text-align: center;
  }
  
  @media (max-width: 768px) {
    .header-text {
      font-size: 1.5rem;
    }
  
    .group-name {
      font-size: 1.1rem;
    }
  
    .card {
      max-width: 100px;
      font-size: 0.8rem; /* Adjust text size for smaller screens */
    }
  
    .card h4 {
      font-size: 0.9rem; /* Adjust text size for smaller screens */
    }
  
    .card p {
      font-size: 0.7rem; /* Adjust text size for smaller screens */
    }
  
    .member-image {
      width: 50px;
      height: 50px;
    }
  }
  
  @media (max-width: 480px) {
    .header-text {
      font-size: 1.2rem;
    }
  
    .group-name {
      font-size: 1rem;
    }
  
    .card {
      max-width: 80px;
      font-size: 0.7rem; /* Adjust text size for smaller screens */
    }
  
    .card h4 {
      font-size: 0.8rem; /* Adjust text size for smaller screens */
    }
  
    .card p {
      font-size: 0.6rem; /* Adjust text size for smaller screens */
    }
  
    .member-image {
      width: 40px;
      height: 40px;
    }
  }
  </style>
  