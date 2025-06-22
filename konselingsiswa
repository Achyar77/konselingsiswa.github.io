<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistem Pencatatan Konseling Siswa</title>
    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <!-- Font Awesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google API Client -->
    <script src="https://apis.google.com/js/api.js"></script>
    <style>
        body {
            background-color: #f8f9fa;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        .sidebar {
            min-height: 100vh;
            background-color: #343a40;
        }
        .sidebar .nav-link {
            color: rgba(255, 255, 255, 0.8);
            margin-bottom: 5px;
        }
        .sidebar .nav-link:hover {
            color: #fff;
            background-color: rgba(255, 255, 255, 0.1);
        }
        .sidebar .nav-link.active {
            color: #fff;
            background-color: #007bff;
        }
        .card-header {
            background-color: #007bff;
            color: white;
        }
        .google-btn {
            background-color: #4285F4;
            color: white;
            border: none;
        }
        .google-btn:hover {
            background-color: #3367D6;
            color: white;
        }
        .logout-btn {
            background-color: #DB4437;
            color: white;
            border: none;
        }
        .logout-btn:hover {
            background-color: #C1351A;
            color: white;
        }
        .form-container {
            background-color: white;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            padding: 20px;
        }
        #googleSignInButton {
            width: 200px;
            height: 40px;
            background-color: #4285F4;
            color: white;
            border-radius: 2px;
            box-shadow: 0 2px 4px 0 rgba(0,0,0,.25);
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .user-avatar {
            width: 32px;
            height: 32px;
            border-radius: 50%;
            margin-right: 10px;
        }
    </style>
</head>
<body>
    <div class="container-fluid">
        <div class="row">
            <!-- Sidebar -->
            <div class="col-md-3 col-lg-2 d-md-block sidebar collapse bg-dark">
                <div class="position-sticky pt-3">
                    <div class="text-center mb-4">
                        <i class="fas fa-user-graduate fa-3x text-white mb-2"></i>
                        <h4 class="text-white">Konseling Siswa</h4>
                        <div id="googleSignInButton" class="d-flex justify-content-center mt-3">
                            <span>Sign In with Google</span>
                        </div>
                        <div id="userInfo" class="text-white mt-3 d-none">
                            <div class="d-flex align-items-center justify-content-center mb-2">
                                <img id="userImage" class="user-avatar">
                                <span id="userName"></span>
                            </div>
                            <button id="signOutButton" class="btn btn-sm logout-btn">
                                <i class="fas fa-sign-out-alt"></i> Logout
                            </button>
                        </div>
                    </div>
                    <ul class="nav flex-column">
                        <li class="nav-item">
                            <a class="nav-link active" href="#dashboard" data-bs-toggle="tab">
                                <i class="fas fa-tachometer-alt me-2"></i>Dashboard
                            </a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="#data-siswa" data-bs-toggle="tab">
                                <i class="fas fa-users me-2"></i>Data Siswa
                            </a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="#tambah-data" data-bs-toggle="tab">
                                <i class="fas fa-plus-circle me-2"></i>Tambah Data
                            </a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="#laporan" data-bs-toggle="tab">
                                <i class="fas fa-chart-bar me-2"></i>Laporan
                            </a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="#google-docs" data-bs-toggle="tab">
                                <i class="fab fa-google-drive me-2"></i>Google Docs
                            </a>
                        </li>
                    </ul>
                </div>
            </div>

            <!-- Main Content -->
            <main class="col-md-9 ms-sm-auto col-lg-10 px-md-4 py-4">
                <div class="tab-content">
                    <!-- Dashboard Tab -->
                    <div class="tab-pane fade show active" id="dashboard">
                        <div class="d-flex justify-content-between flex-wrap flex-md-nowrap align-items-center pt-3 pb-2 mb-3 border-bottom">
                            <h1 class="h2">Dashboard Konseling</h1>
                            <div class="btn-toolbar mb-2 mb-md-0">
                                <div class="btn-group me-2">
                                    <button type="button" class="btn btn-sm btn-outline-secondary">
                                        <i class="fas fa-calendar me-1"></i>Hari Ini
                                    </button>
                                    <button type="button" class="btn btn-sm btn-outline-secondary">
                                        <i class="fas fa-calendar-week me-1"></i>Minggu Ini
                                    </button>
                                </div>
                            </div>
                        </div>

                        <div class="row mb-4">
                            <div class="col-md-4">
                                <div class="card text-white bg-primary mb-3">
                                    <div class="card-body">
                                        <div class="d-flex justify-content-between align-items-center">
                                            <div>
                                                <h6 class="card-title">Total Konseling</h6>
                                                <h2 class="card-text" id="total-konseling">0</h2>
                                            </div>
                                            <i class="fas fa-clipboard-list fa-3x opacity-50"></i>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <div class="col-md-4">
                                <div class="card text-white bg-success mb-3">
                                    <div class="card-body">
                                        <div class="d-flex justify-content-between align-items-center">
                                            <div>
                                                <h6 class="card-title">Siswa Aktif</h6>
                                                <h2 class="card-text" id="siswa-aktif">0</h2>
                                            </div>
                                            <i class="fas fa-user-graduate fa-3x opacity-50"></i>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <div class="col-md-4">
                                <div class="card text-white bg-warning mb-3">
                                    <div class="card-body">
                                        <div class="d-flex justify-content-between align-items-center">
                                            <div>
                                                <h6 class="card-title">Kasus Terbanyak</h6>
                                                <h2 class="card-text" id="kasus-terbanyak">-</h2>
                                            </div>
                                            <i class="fas fa-exclamation-triangle fa-3x opacity-50"></i>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <div class="card mb-4">
                            <div class="card-header">
                                <i class="fas fa-chart-line me-1"></i>
                                Grafik Konseling Bulan Ini
                            </div>
                            <div class="card-body">
                                <canvas id="konselingChart" height="300"></canvas>
                            </div>
                        </div>
                    </div>

                    <!-- Data Siswa Tab -->
                    <div class="tab-pane fade" id="data-siswa">
                        <div class="d-flex justify-content-between flex-wrap flex-md-nowrap align-items-center pt-3 pb-2 mb-3 border-bottom">
                            <h1 class="h2">Data Siswa Konseling</h1>
                            <div class="btn-toolbar mb-2 mb-md-0">
                                <div class="input-group">
                                    <input type="text" class="form-control" placeholder="Cari siswa..." id="searchInput">
                                    <button class="btn btn-outline-secondary" type="button" id="searchButton">
                                        <i class="fas fa-search"></i>
                                    </button>
                                </div>
                            </div>
                        </div>

                        <div class="table-responsive">
                            <table class="table table-striped table-hover">
                                <thead>
                                    <tr>
                                        <th>No</th>
                                        <th>NIS</th>
                                        <th>Nama Siswa</th>
                                        <th>Kelas</th>
                                        <th>Tanggal Konseling</th>
                                        <th>Jenis Masalah</th>
                                        <th>Status</th>
                                        <th>Aksi</th>
                                    </tr>
                                </thead>
                                <tbody id="siswaTableBody">
                                    <!-- Data akan diisi oleh JavaScript -->
                                </tbody>
                            </table>
                        </div>

                        <nav aria-label="Page navigation" class="mt-4">
                            <ul class="pagination justify-content-center">
                                <li class="page-item disabled">
                                    <a class="page-link" href="#" tabindex="-1" aria-disabled="true">Sebelumnya</a>
                                </li>
                                <li class="page-item active"><a class="page-link" href="#">1</a></li>
                                <li class="page-item"><a class="page-link" href="#">2</a></li>
                                <li class="page-item"><a class="page-link" href="#">3</a></li>
                                <li class="page-item">
                                    <a class="page-link" href="#">Selanjutnya</a>
                                </li>
                            </ul>
                        </nav>
                    </div>

                    <!-- Tambah Data Tab -->
                    <div class="tab-pane fade" id="tambah-data">
                        <div class="d-flex justify-content-between flex-wrap flex-md-nowrap align-items-center pt-3 pb-2 mb-3 border-bottom">
                            <h1 class="h2">Tambah Data Konseling</h1>
                        </div>

                        <div class="form-container">
                            <form id="konselingForm">
                                <div class="row mb-3">
                                    <div class="col-md-6">
                                        <label for="nis" class="form-label">NIS</label>
                                        <input type="text" class="form-control" id="nis" required>
                                    </div>
                                    <div class="col-md-6">
                                        <label for="nama" class="form-label">Nama Siswa</label>
                                        <input type="text" class="form-control" id="nama" required>
                                    </div>
                                </div>

                                <div class="row mb-3">
                                    <div class="col-md-4">
                                        <label for="kelas" class="form-label">Kelas</label>
                                        <select class="form-select" id="kelas" required>
                                            <option value="" selected disabled>Pilih Kelas</option>
                                            <option value="X">X</option>
                                            <option value="XI">XI</option>
                                            <option value="XII">XII</option>
                                        </select>
                                    </div>
                                    <div class="col-md-4">
                                        <label for="jurusan" class="form-label">Jurusan</label>
                                        <select class="form-select" id="jurusan" required>
                                            <option value="" selected disabled>Pilih Jurusan</option>
                                            <option value="IPA">IPA</option>
                                            <option value="IPS">IPS</option>
                                            <option value="Bahasa">Bahasa</option>
                                            <option value="Agama">Agama</option>
                                        </select>
                                    </div>
                                    <div class="col-md-4">
                                        <label for="tanggal" class="form-label">Tanggal Konseling</label>
                                        <input type="date" class="form-control" id="tanggal" required>
                                    </div>
                                </div>

                                <div class="mb-3">
                                    <label for="masalah" class="form-label">Jenis Masalah</label>
                                    <select class="form-select" id="masalah" required>
                                        <option value="" selected disabled>Pilih Jenis Masalah</option>
                                        <option value="Akademik">Akademik</option>
                                        <option value="Perilaku">Perilaku</option>
                                        <option value="Sosial">Sosial</option>
                                        <option value="Keluarga">Keluarga</option>
                                        <option value="Karir">Karir</option>
                                        <option value="Lainnya">Lainnya</option>
                                    </select>
                                </div>

                                <div class="mb-3">
                                    <label for="deskripsi" class="form-label">Deskripsi Masalah</label>
                                    <textarea class="form-control" id="deskripsi" rows="3" required></textarea>
                                </div>

                                <div class="mb-3">
                                    <label for="solusi" class="form-label">Solusi/Tindakan</label>
                                    <textarea class="form-control" id="solusi" rows="3" required></textarea>
                                </div>

                                <div class="mb-3">
                                    <label for="status" class="form-label">Status</label>
                                    <select class="form-select" id="status" required>
                                        <option value="Belum selesai">Belum selesai</option>
                                        <option value="Dalam proses">Dalam proses</option>
                                        <option value="Selesai">Selesai</option>
                                    </select>
                                </div>

                                <div class="d-grid gap-2 d-md-flex justify-content-md-end">
                                    <button type="reset" class="btn btn-secondary me-md-2">
                                        <i class="fas fa-undo me-1"></i>Reset
                                    </button>
                                    <button type="submit" class="btn btn-primary">
                                        <i class="fas fa-save me-1"></i>Simpan Data
                                    </button>
                                </div>
                            </form>
                        </div>
                    </div>

                    <!-- Laporan Tab -->
                    <div class="tab-pane fade" id="laporan">
                        <div class="d-flex justify-content-between flex-wrap flex-md-nowrap align-items-center pt-3 pb-2 mb-3 border-bottom">
                            <h1 class="h2">Laporan Konseling</h1>
                            <div class="btn-toolbar mb-2 mb-md-0">
                                <div class="btn-group me-2">
                                    <button type="button" class="btn btn-sm btn-outline-secondary" id="printReport">
                                        <i class="fas fa-print me-1"></i>Cetak
                                    </button>
                                    <button type="button" class="btn btn-sm btn-outline-secondary" id="exportReport">
                                        <i class="fas fa-file-export me-1"></i>Export
                                    </button>
                                </div>
                            </div>
                        </div>

                        <div class="card mb-4">
                            <div class="card-header">
                                <i class="fas fa-filter me-1"></i>
                                Filter Laporan
                            </div>
                            <div class="card-body">
                                <form id="filterForm">
                                    <div class="row mb-3">
                                        <div class="col-md-4">
                                            <label for="filterTanggalMulai" class="form-label">Tanggal Mulai</label>
                                            <input type="date" class="form-control" id="filterTanggalMulai">
                                        </div>
                                        <div class="col-md-4">
                                            <label for="filterTanggalSelesai" class="form-label">Tanggal Selesai</label>
                                            <input type="date" class="form-control" id="filterTanggalSelesai">
                                        </div>
                                        <div class="col-md-4">
                                            <label for="filterKelas" class="form-label">Kelas</label>
                                            <select class="form-select" id="filterKelas">
                                                <option value="" selected>Semua Kelas</option>
                                                <option value="X">X</option>
                                                <option value="XI">XI</option>
                                                <option value="XII">XII</option>
                                            </select>
                                        </div>
                                    </div>
                                    <div class="row mb-3">
                                        <div class="col-md-6">
                                            <label for="filterMasalah" class="form-label">Jenis Masalah</label>
                                            <select class="form-select" id="filterMasalah">
                                                <option value="" selected>Semua Jenis</option>
                                                <option value="Akademik">Akademik</option>
                                                <option value="Perilaku">Perilaku</option>
                                                <option value="Sosial">Sosial</option>
                                                <option value="Keluarga">Keluarga</option>
                                                <option value="Karir">Karir</option>
                                                <option value="Lainnya">Lainnya</option>
                                            </select>
                                        </div>
                                        <div class="col-md-6">
                                            <label for="filterStatus" class="form-label">Status</label>
                                            <select class="form-select" id="filterStatus">
                                                <option value="" selected>Semua Status</option>
                                                <option value="Belum selesai">Belum selesai</option>
                                                <option value="Dalam proses">Dalam proses
