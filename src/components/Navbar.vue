<template>
    <nav class="navbar navbar-expand-lg navbar-light bg-light fixed-top">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">CryptoBro</a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0"></ul>
        
      </div>
    </div>
  </nav>
</template>
<style scoped>
.table {
  margin-top: 80px;
  width: 100%;
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.table th, .table td {
  text-align: center;
  vertical-align: middle;
}

.table thead {
  background-color: #4275af;
  color: white;
  font-weight: bold;
}

.table tbody tr:hover {
  background-color: #f1f1f1;
}

.table-bordered {
  border: 1px solid #ddd;
}

.table-striped tbody tr:nth-child(odd) {
  background-color: #f9f9f9;
}

.table-hover tbody tr:hover {
  background-color: #e9ecef;
}

.container {
  padding-top: 80px;
}

.navbar {
  background-color: #4275af !important; 
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); 
  transition: all 0.3s ease; 
}

.navbar-brand {
  font-size: 1.5rem;
  font-weight: bold;
  color: #fff !important;
}

.navbar-nav .nav-link {
  color: #fff !important;
  font-weight: 500;
  padding: 8px 15px;
  border-radius: 5px; 
}

.navbar-nav .nav-link:hover {
  background-color: rgba(255, 255, 255, 0.2); 
}

.form-control {
  border-radius: 25px; 
  border: 2px solid #4275af;
}

.form-control:focus {
  border-color: #4275af;
  box-shadow: 0 0 5px rgba(52, 168, 83, 0.5);
}

.btn-outline-success {
  color: #fff;
  border-color: #fff;
}

.btn-outline-success:hover {
  background-color: #fff;
  color: #4275af;
  border-color: #fff;
}
</style>